# Tasks
- [x] Task 1: 创建 `.trae/skills/frp-panel.md` 技能文件
  - [x] SubTask 1.1: 编写项目概述章节（项目定位、核心优势、架构图说明）
  - [x] SubTask 1.2: 编写架构概览与目录结构章节（三端架构、技术栈、关键目录说明）
  - [x] SubTask 1.3: 编写快速开始与部署章节（Docker Compose 部署为主，含 docker-compose.yaml 样板、host 网络模式、数据卷挂载、环境变量注入、Master/Server/Client 三种启动命令、systemd 服务安装）
  - [x] SubTask 1.4: 编写 frps 配置使用说明章节（服务端 WebUI 配置步骤、default 服务端与独立 server 区别、高级模式 JSON 配置格式、代理端口范围规划、frps_url 配置说明）
  - [x] SubTask 1.5: 编写 frpc 配置使用说明章节（客户端 WebUI 配置步骤、基础/高级模式切换、frps_url 多服务端连接配置、隧道类型选择、客户端多实例说明）
  - [x] SubTask 1.6: 编写 WireGuard 智能组网配置使用说明章节（概念模型：网络→设备→端点→连接、环境准备 sysctl 配置、创建网络/CIDR/ACL、创建端点/UDP vs WebSocket、创建设备/接口名称/IP/标签/端点绑定、创建连接的步骤、拓扑图查看与手动优化、带宽权重配置）
  - [x] SubTask 1.7: 编写 REST API 完整参考章节（Auth/User/Platform/Client/Server/FRPC/FRPS/Proxy/Worker/WG 共 10 个模块，每个模块列出所有端点、请求/响应格式）
  - [x] SubTask 1.8: 编写 gRPC 接口参考章节（Master service 的 10 个 RPC 方法说明和 Event 事件枚举）
  - [x] SubTask 1.9: 编写数据模型速查章节（Client/Server/ProxyConfig/ProxyInfo/Worker/Network/Endpoint/WireGuardConfig/WireGuardLink 等核心模型）
  - [x] SubTask 1.10: 编写配置项速查章节（所有环境变量及其默认值、用途说明，含 APP_*/MASTER_*/SERVER_*/DB_*/CLIENT_*/CLIENT_WORKER_*/CLIENT_FEATURES_*/LOGGER_*/DEBUG_* 分区）
  - [x] SubTask 1.11: 编写开发指南章节（编译命令 go build、proto 代码生成 codegen.sh、前端开发 pnpm dev）

# Task Dependencies
- 所有 SubTask 互相独立，可并行编写，最终合并为单一技能文件