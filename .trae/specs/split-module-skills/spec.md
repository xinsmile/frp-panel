# 拆分 FRP-Panel 模块化技能文件 Spec

## Why
当前 `.trae/skills/frp-panel.md` 是一个约 1000 行的单文件，包含所有模块的 API 文档、配置说明、部署指南等。当 AI 助手需要查询特定模块（如 Proxy 的 API 接口）时，需要加载整个文件，效率低下。拆分为模块化技能文件后，每个文件专注一个领域，AI 助手可按需加载，且每个 API 接口的请求路径、请求参数、返回结果格式齐全。

## What Changes
- 新增 `.trae/skills/frp-panel/` 目录，包含以下 13 个模块化技能文件：
  - `01-overview.md` — 项目概述 + 架构概览 + 目录结构
  - `02-deployment.md` — 部署指南（Docker Compose / 直接安装 / systemd / 反向代理 TLS）
  - `03-frps-config.md` — frps 配置使用说明（WebUI 操作步骤、default vs 独立 server、端口规划、高级模式 JSON）
  - `04-frpc-config.md` — frpc 配置使用说明（WebUI 操作步骤、frps_url 连接、隧道类型、插件、远程升级）
  - `05-wireguard.md` — WireGuard 智能组网配置使用说明（概念模型、环境准备、逐步创建指南、拓扑优化、ACL 语法）
  - `06-api-auth.md` — Auth 模块 REST API 完整文档（login/register/logout/cert/sign-token）
  - `07-api-user.md` — User 模块 REST API 完整文档（get/update/sign-token）
  - `08-api-platform.md` — Platform 模块 REST API 完整文档（baseinfo/clientsstatus）
  - `09-api-client-server.md` — Client + Server 模块 REST API 完整文档（CRUD/init/upgrade）
  - `10-api-frpc-frps.md` — FRPC + FRPS 模块 REST API 完整文档（update/remove/start/stop）
  - `11-api-proxy.md` — Proxy 模块 REST API 完整文档（CRUD 配置/启动停止/流量统计）
  - `12-api-worker.md` — Worker 模块 REST API 完整文档（CRUD/状态/Ingress/安装Workerd）
  - `13-api-wireguard.md` — WireGuard 模块 REST API 完整文档（Network/Endpoint/Link/WireGuard 完整 CRUD + 拓扑 + 运行时）
- 保留原有 `frp-panel.md` 作为总索引文件，链接到各模块技能文件
- 每个 API 模块技能文件必须包含：端点路径、HTTP 方法、请求参数（字段名、类型、必填/可选、说明）、响应结构（字段名、类型、说明）

## Impact
- Affected specs: 无（新增技能）
- Affected code: 仅新增 `.trae/skills/frp-panel/` 目录下的 13 个文件，以及修改 `frp-panel.md` 为索引文件

## ADDED Requirements

### Requirement: 模块化技能文件拆分
系统 SHALL 将 `frp-panel.md` 拆分为 13 个模块化技能文件，按功能领域组织。

#### Scenario: 查询 Proxy API 接口
- **WHEN** 开发者询问 "如何调用创建代理配置的 API"
- **THEN** AI 助手能加载 `11-api-proxy.md`，给出 `/api/v1/proxy/create_config` 的完整请求参数和响应格式

#### Scenario: 查询 WireGuard 组网步骤
- **WHEN** 开发者询问 "如何配置 WireGuard 智能组网"
- **THEN** AI 助手能加载 `05-wireguard.md`，给出环境准备、概念说明、逐步创建步骤

### Requirement: API 文档完整性
每个 API 模块技能文件 SHALL 包含：
- 端点路径（如 `/api/v1/proxy/create_config`）
- HTTP 方法（POST/GET）
- 认证要求（JWT/否）
- 请求参数表（字段名、Protobuf 类型、Go 类型、必填/可选、说明）
- 响应结构表（字段名、Protobuf 类型、Go 类型、说明）
- Protobuf 消息定义原文引用

### Requirement: 总索引文件
`frp-panel.md` SHALL 更新为总索引文件，列出所有 13 个模块技能文件的名称、路径和简要说明。