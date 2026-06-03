# 创建 FRP-Panel 项目知识技能 Spec

## Why
FRP-Panel 是一个功能丰富的 FRP 可视化管理面板，包含 Master/Server/Client 三端架构、REST API + gRPC 双协议、WireGuard 智能组网、Edge Worker 等复杂子系统。当前项目文档分散在 docs/ 目录和代码注释中，开发者（包括 AI 助手）在修改代码时需要快速查阅项目架构、API 接口定义和使用手册。创建项目知识技能可以让 AI 助手更准确地理解项目并提供开发协助。

## What Changes
- 新增 `.trae/skills/frp-panel.md` — FRP-Panel 项目知识技能文件，包含：
  - 项目架构概览（三端架构、技术栈、目录结构）
  - 部署与使用手册（Docker部署、环境变量、Master/Server/Client启动命令、部署流程）
  - frps 配置使用说明（服务端配置项、高级模式JSON配置、default服务端配置注意事项）
  - frpc 配置使用说明（客户端配置项、高级模式JSON配置、多服务端连接配置）
  - WireGuard 智能组网配置使用说明（概念介绍、环境准备、网络/端点/设备/连接创建步骤、ACL配置、拓扑优化）
  - Docker 部署配置使用说明（docker-compose.yaml样板、host网络模式、数据卷挂载、环境变量注入）
  - 完整 REST API 接口文档（所有 /api/v1/* 端点的请求/响应格式）
  - gRPC 接口文档（Master service 的 RPC 方法说明）
  - 数据模型说明（Client/Server/ProxyConfig/Worker/WireGuard 等模型）
  - Protobuf 消息类型速查
  - 配置项速查表
  - 开发指南（编译、代码生成、前端开发）

## Impact
- Affected specs: 无（新增技能）
- Affected code: 仅新增 `.trae/skills/frp-panel.md`，不修改任何现有代码

## ADDED Requirements
### Requirement: 项目知识技能
系统 SHALL 提供一个 `frp-panel.md` 技能文件，使 AI 助手能够在开发时快速理解项目架构、API 接口和使用方法。

#### Scenario: 查询 REST API 接口
- **WHEN** 开发者询问 "如何调用创建代理配置的 API"
- **THEN** AI 助手能根据技能文件中的 API 文档，给出 `/api/v1/proxy/create_config` 的完整请求/响应格式

#### Scenario: 理解项目架构
- **WHEN** 开发者询问 "Master 和 Client 之间如何通信"
- **THEN** AI 助手能根据技能文件中的架构说明，解释 gRPC 双向流通信机制

#### Scenario: 查询部署配置
- **WHEN** 开发者询问 "MASTER_RPC_HOST 环境变量是什么"
- **THEN** AI 助手能根据技能文件中的配置速查表给出准确答案

### Requirement: 技能文件内容完整性
技能文件 SHALL 包含以下章节：
1. 项目概述
2. 架构概览与目录结构
3. 快速开始与部署（Docker部署为主，含docker-compose.yaml样板、host网络模式说明）
4. frps 配置使用说明（服务端WebUI配置步骤、高级模式JSON配置、default服务端注意事项、代理端口范围规划）
5. frpc 配置使用说明（客户端WebUI配置步骤、高级模式JSON配置、frps_url多服务端连接、隧道类型选择）
6. WireGuard 智能组网配置使用说明（概念模型、环境准备sysctl配置、创建网络/端点/设备/连接的完整步骤、ACL配置语法、拓扑查看与手动优化）
7. REST API 完整参考（按模块分组）
8. gRPC 接口参考
9. 数据模型速查
10. 配置项速查（含Client TLS/Worker/Features配置）
11. 开发指南

#### Scenario: 查询 WireGuard 智能组网配置
- **WHEN** 开发者询问 "如何配置 WireGuard 智能组网"
- **THEN** AI 助手能根据技能文件给出环境准备、概念说明、逐步创建步骤

#### Scenario: 查询 frps 配置
- **WHEN** 开发者询问 "如何配置 frps 服务端"
- **THEN** AI 助手能根据技能文件给出 WebUI 操作步骤和高级模式 JSON 配置说明

#### Scenario: 查询 frpc 配置
- **WHEN** 开发者询问 "如何配置 frpc 客户端"
- **THEN** AI 助手能根据技能文件给出 WebUI 操作步骤和高级模式 JSON 配置说明

#### Scenario: 查询 Docker 部署配置
- **WHEN** 开发者询问 "如何使用 Docker 部署 frp-panel"
- **THEN** AI 助手能根据技能文件给出 docker-compose.yaml 样板和环境变量配置说明