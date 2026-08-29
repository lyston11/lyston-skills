# Placement And Naming

Invariants for choosing where a document lives and what it is called. Apply these with any mutating route; the active workflow owns the step order.

## Placement Model

The active Codex vault uses a **category-first, primary-subject-second** hierarchy:

```text
Codex/
  项目与服务/
    Hermes/
      Hermes Ubuntu 服务器部署记录（lyston11.qzz.io）.md
    Sub2API/
      Sub2API OrbStack 本机部署记录（lystonmacbook-pro.local）.md
  Agent 与 AI 系统/
    Pi/
      Pi 上下文压缩与项目记忆工具选型.md
  Skills 与插件/
    find-code-simplifications/
      find-code-simplifications skill 用途与触发机制.md
  软件与工具/
    Obsidian/
      Obsidian 多设备同步与 AI 写作系统完全指南.md
  终端与命令行/
    Ghostty/
      Ghostty 配置修复记录（lystondeMacBook-Air.local）.md
  开发环境/
    OrbStack/
      OrbStack 介绍与使用（lystondeMacBook-Air.local）.md
  网络与访问/
    Tailscale/
      Tailscale 跨平台 SSH 连接完全指南.md
  服务器与云平台/
    DigitalOcean/
      DigitalOcean Ubuntu 服务器初始化与基础运维（lyston11.qzz.io）.md
  学习与研究/
    知识库与 RAG/
      00 知识库与 RAG 学习路线.md
```

The first-level folder is a stable category. The second-level folder is the ownership boundary for the actual project, service, product, agent, skill, plugin, application, tool, environment, network technology, cloud platform, or learning topic.

Do not create a new first-level folder for every new subject. Create a second-level subject folder inside one of the fixed categories below. A new first-level category requires explicit user approval or clear evidence that every existing category is semantically wrong.

## Fixed First-Level Categories

Use these category names exactly:

| First-level category | What belongs here | Typical subjects |
|---|---|---|
| `项目与服务` | User-owned projects, products, applications, deployed services, customer work, and stable business workstreams | Hermes, Sub2API, Fast Note Sync, DBX, HAPI, Smart Seat, 锐鲨, 天命AI写作 |
| `Agent 与 AI 系统` | Standalone AI agents, agent runtimes, coding agents, model gateways, orchestration systems, and AI operating environments | Codex, Pi, Claude Code, GenericAgent, OpenClaw, MindOS, HelloKimi |
| `Skills 与插件` | Reusable skills, plugins, extensions, MCP add-ons, and host-independent integration packages | find-code-simplifications, claudian, a Claude Code skill, an Obsidian plugin |
| `软件与工具` | Standalone desktop apps, web tools, developer utilities, document tools, platforms, and general-purpose software | Obsidian, MarkEdit, GitHub, video download tools |
| `终端与命令行` | Terminal emulators, shells, terminal file managers, CLI navigation tools, tmux, and terminal workflows | Ghostty, Warp, Yazi, zoxide, Oh My Zsh, tmux |
| `开发环境` | Virtualization, local container runtimes, OS subsystems, language/package environments, IDE environments, and remote-development setups | OrbStack, Hyper-V, WSL, Python 环境管理, 远程开发 |
| `网络与访问` | VPNs, overlay networks, proxies, tunnels, DNS, reverse proxies, remote access, and access control not owned by one project or host | Tailscale, Cloudflare, SSH access, Nginx routing |
| `服务器与云平台` | Cloud providers, server initialization, host baselines, server-specific operations, and multi-service infrastructure tied to one host or provider | DigitalOcean, Oracle Cloud, 1Panel server operations |
| `学习与研究` | Learning tracks, conceptual notes, technology research, and comparisons with no operational owner | 知识库与 RAG, 数据库, Kubernetes, general LLM research |

Do not create broad catch-all first-level folders such as `其他`, `杂项`, `综合`, or `基础设施`. `服务器与云平台` and `网络与访问` are scoped categories, not dumping grounds.

## Classification Precedence

These rules are ordered. The first rule that clearly owns the document wins.

1. **Explicit destination wins.** If the user gives an exact file or folder path, use it.
2. **Project ownership wins over implementation technology.** A project deployment, project database, project tunnel, or project-specific plugin belongs under `项目与服务/<project>/`, even if it uses Docker, Cloudflare, Tailscale, MySQL, or a specific server.
3. **The subject's intrinsic role wins over the document genre.** A tutorial about Ghostty still belongs under `终端与命令行/Ghostty/`; it does not move to `学习与研究` merely because it teaches.
4. **Standalone skill or plugin wins over its host integration.** A document mainly about one reusable plugin or skill belongs under `Skills 与插件/<subject>/`. A small host-specific setting that is only one section of an existing host guide stays with the host guide.
5. **Specific technical categories beat general software.** Terminal tools go to `终端与命令行`; runtimes and virtualized environments go to `开发环境`; network technologies go to `网络与访问`; host/provider operations go to `服务器与云平台`. Use `软件与工具` only when no more specific category fits.
6. **Server-specific operations beat generic network classification.** A reverse-proxy configuration unique to one DigitalOcean host belongs under `服务器与云平台/DigitalOcean/`; a reusable Tailscale or Nginx guide belongs under `网络与访问/<subject>/`.
7. **Learning is the final conceptual fallback.** Use `学习与研究` only when no project, product, tool, runtime, network technology, server platform, agent, skill, or plugin owns the note.
8. **Devices and environments never determine the category.** Put them in the filename suffix and document metadata, not in a root folder.

Collision examples:

```text
项目与服务/Sub2API/Sub2API Cloudflare Tunnel 外网访问配置记录（lyston.qzz.io）.md
  # Project ownership wins over 网络与访问.

Agent 与 AI 系统/Pi/Pi 插件用途与使用指南（lystondeMacBook-Air.local）.md
  # The document is about Pi's own plugin ecosystem, not one reusable standalone plugin.

Skills 与插件/find-code-simplifications/find-code-simplifications skill 用途与触发机制.md
  # The standalone reusable skill is the subject.

终端与命令行/Ghostty/Ghostty 与 Oh My Zsh 配置指南（lystondeMacBook-Air.local）.md
  # Terminal category is more specific than 软件与工具.

服务器与云平台/DigitalOcean/lyston11.qzz.io 子域名反代配置记录（lyston11.qzz.io）.md
  # The configuration is unique to this host and operates several services.

网络与访问/Tailscale/Tailscale 原理与用途说明.md
  # Reusable network-technology documentation.
```

## Category And Subject Decision Test

Apply this test in order and stop at the first clear answer:

1. **Explicit destination:** Did the user explicitly name a file or folder?
2. **Primary owner:** Which subject owns the document after removing incidental hosts, authoring agents, and integrations?
3. **Project check:** Is the document operationally specific to an owned project or service? If yes, use `项目与服务/<project>/`.
4. **Category check:** Which fixed category describes the subject's intrinsic role?
5. **Subject check:** Does that category already contain the canonical subject folder?
6. **Weak-link rejection:** Is the proposed destination related only through authorship, installation host, plugin host, compatibility, or a shared keyword? If yes, reject it.
7. **Create at level two:** If no strong subject match exists, create `<fixed category>/<canonical subject>/`, not a new root folder.

File counts, folder age, recency, prior accidental placement, and keyword-hit counts are not ownership evidence.

## Subject Folder Rules

- Use the canonical subject name for the second-level folder: `Ghostty`, `Tailscale`, `DigitalOcean`, `Hermes`, or `find-code-simplifications`.
- Keep all documents whose durable value belongs to the same subject in that subject folder.
- Preserve deeper subfolders only for real subprojects, modules, or substantial learning series. Do not add a third level merely to classify document types such as `指南`, `故障`, or `部署`.
- A comparison or collection with no single named product may use a stable neutral subject folder such as `软件与工具/视频下载/` or `学习与研究/本地 LLM/`.
- Do not create second-level folders named only after a device, hostname, server, operating system, runtime, date, or document type. A cloud provider or stable platform such as `DigitalOcean`, `Oracle Cloud`, `WSL`, or `OrbStack` is a valid subject.
- Do not route a subject into an agent folder merely because that agent authored, installed, or mentioned it.

## Filename Device Suffix

Every operational, deployment, troubleshooting, access, tunnel, proxy, configuration, or environment-specific document must end with a device/environment suffix before `.md`:

```text
主题（设备或环境）.md
```

Examples:

```text
项目与服务/Hermes/Hermes WebUI 下线与清理记录（lyston11.qzz.io）.md
项目与服务/Sub2API/Sub2API Docker 部署记录（OrbStack）.md
终端与命令行/Ghostty/Ghostty 配置修复记录（lystondeMacBook-Air.local）.md
服务器与云平台/DigitalOcean/DigitalOcean Ubuntu 服务器初始化与基础运维（lyston11.qzz.io）.md
网络与访问/Cloudflare/Cloudflare Tunnel 外网访问配置记录（lystondeMacBook-Air.local）.md
Agent 与 AI 系统/Codex/Codex 会话同步与迁移指南（lystondeMacBook-Air.local）.md
```

Use the most useful marker for the suffix:

- Hostname or device name: `lystondeMacBook-Air.local`, `lystonmacbook-pro.local`, `lyston11.qzz.io`.
- Deployment environment: `Ubuntu srv-projects`, `OrbStack`, `Cloudflare Tunnel`.
- Domain or public endpoint when it identifies the environment better than the hostname.

Do not rely only on frontmatter or body metadata to distinguish devices. Documents that are purely conceptual, creative, project-agnostic, or study-oriented may omit the suffix when no environment ownership exists.

## Naming

Use Chinese filenames and headings when the user writes in Chinese or the document is mainly Chinese. Use clear, short Markdown filenames.

- First-level folders use the exact fixed category names.
- Second-level folders use the canonical project, product, service, agent, tool, skill, plugin, platform, or topic name.
- Preserve recognizable capitalization such as `Pi`, `Trellis`, `Magic Context`, `Ghostty`, or `DigitalOcean`.
- Do not prefix a standalone subject with `Codex`, `Pi`, or another agent merely to indicate where it was used.
- Do not name category or subject folders after dates or document types such as `部署记录`, `故障排查`, or `教程`.

## Environment Metadata

For operational documents, include ownership/context near the top when relevant:

- Hostname or device name.
- OS, cloud provider, or platform.
- Main domain/IP, if public.
- Deployment root path.
- Container/runtime context.
- Whether the record is local desktop, server-side, container-only, or tunnel/reverse-proxy related.

The metadata supports the filename suffix; it does not replace it.
