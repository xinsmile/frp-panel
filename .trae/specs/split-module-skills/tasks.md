# Tasks
- [x] Task 1: 创建索引文件 + 项目概述技能（`01-overview.md` + `frp-panel.md` 更新为索引）
  - [x] SubTask 1.1: 提取现有 `frp-panel.md` 的第1-2章内容（项目概述、架构概览、目录结构）到 `01-overview.md`
  - [x] SubTask 1.2: 更新 `frp-panel.md` 为总索引文件，列出 13 个模块的路径和简要说明

- [x] Task 2: 创建部署指南技能（`02-deployment.md`）
  - [x] SubTask 2.1: 提取现有第3章（Docker Compose 部署、直接运行安装、反向代理 TLS、systemd 服务安装）

- [x] Task 3: 创建 frps 配置技能（`03-frps-config.md`）
  - [x] SubTask 3.1: 提取现有第4章（WebUI 操作步骤、default vs 独立 server、配置编辑、端口规划）

- [x] Task 4: 创建 frpc 配置技能（`04-frpc-config.md`）
  - [x] SubTask 4.1: 提取现有第5章（WebUI 操作步骤、frps_url 连接、隧道管理、插件类型、远程升级）

- [x] Task 5: 创建 WireGuard 组网技能（`05-wireguard.md`）
  - [x] SubTask 5.1: 提取现有第6章并扩展（概念模型、环境准备、逐步骤创建指南、ACL 语法、拓扑优化、端点类型对比）

- [x] Task 6: 创建 Auth API 技能（`06-api-auth.md`），包含以下端点的完整请求参数和响应结构：
  - POST `/api/v1/auth/login` - 请求：`{username, password}` → LoginResponse
  - POST `/api/v1/auth/register` - 请求：`{username, password, email}` → RegisterResponse
  - GET `/api/v1/auth/logout` → CommonResponse
  - POST `/api/v1/auth/cert` - 请求：`{client_type, client_id, client_secret}` → GetClientCertResponse
  - POST `/api/v1/user/sign-token` - 请求：`{expires_in, permissions: [{method, path}]}` → SignTokenResponse

- [x] Task 7: 创建 User API 技能（`07-api-user.md`），包含以下端点的完整请求参数和响应结构：
  - POST `/api/v1/user/get` - 请求：`{}` → GetUserInfoResponse（含 User 完整字段）
  - POST `/api/v1/user/update` - 请求：`{user_info: User}` → UpdateUserInfoResponse

- [x] Task 8: 创建 Platform API 技能（`08-api-platform.md`），包含以下端点的完整请求参数和响应结构：
  - GET `/api/v1/platform/baseinfo` → GetPlatformInfoResponse（含 14 个字段）
  - POST `/api/v1/platform/clientsstatus` - 请求：`{client_type, client_ids}` → GetClientsStatusResponse（含 ClientStatus 子结构）

- [x] Task 9: 创建 Client/Server API 技能（`09-api-client-server.md`），包含以下端点的完整请求参数和响应结构：
  - Client: get/init/delete/list/install_workerd/upgrade（共 6 个端点）
  - Server: get/init/delete/list（共 4 个端点）
  - 每个端点列出 Request/Response 的完整字段表

- [x] Task 10: 创建 FRPC/FRPS API 技能（`10-api-frpc-frps.md`），包含以下端点的完整请求参数和响应结构：
  - FRPC: update/remove/stop/start（共 4 个端点）
  - FRPS: update/remove（共 2 个端点）
  - 每个端点列出 Request/Response 的完整字段表

- [x] Task 11: 创建 Proxy API 技能（`11-api-proxy.md`），包含以下端点的完整请求参数和响应结构：
  - get_by_cid / get_by_sid / list_configs / create_config / update_config / delete_config / get_config / start_proxy / stop_proxy（共 9 个端点）
  - 列出 ProxyConfig / ProxyInfo / ProxyWorkingStatus 的完整字段

- [x] Task 12: 创建 Worker API 技能（`12-api-worker.md`），包含以下端点的完整请求参数和响应结构：
  - get / status / create / list / remove / update / redeploy / create_ingress / get_ingress（共 9 个端点）
  - 列出 Worker / Socket 的完整字段

- [x] Task 13: 创建 WireGuard API 技能（`13-api-wireguard.md`），包含以下 4 个子模块的完整请求参数和响应结构：
  - Network: create/delete/update/get/list/topology（共 6 个端点）
  - Endpoint: create/delete/update/get/list（共 5 个端点）
  - WireGuard: create/delete/update/restart/get/list/runtime/get（共 8 个端点）
  - Link: create/delete/update/get/list（共 5 个端点）
  - 列出 Network/Endpoint/WireGuardConfig/WireGuardLink/WGDeviceRuntimeInfo 的完整字段

# Task Dependencies
- Task 1（索引+概述）必须在所有其他 Task 完成后更新索引链接
- Task 2~5（部署/配置/组网）互相独立，可并行
- Task 6~13（8 个 API 模块）互相独立，可并行
- 所有 Task 可并行执行