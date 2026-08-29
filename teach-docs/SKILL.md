---
name: teach-docs
description: Use when creating or revising step-by-step educational Markdown learning documents, especially technical study notes that must teach concepts, mechanisms, commands, usage scenarios, troubleshooting, and deeper systems thinking without changing an existing teaching style.
---

# Teach Docs

## Core Principle

Write learning documents that make the reader understand the system, not just copy commands.

Good teaching docs connect:

```text
scenario -> concept -> mechanism -> command/config -> observation -> pitfall -> checkpoint
```

Use the user's fixed teaching style below as the default style. For existing documents, preserve that style and improve the content from inside the existing chapters.

## Default Save Location

Save teaching Markdown documents in the user's Codex Obsidian study-note space by default:

```text
/Users/lyston/Obsidian/lyston/Codex/学习笔记
```

Use topic folders under that directory:

```text
/Users/lyston/Obsidian/lyston/Codex/学习笔记/Docker
/Users/lyston/Obsidian/lyston/Codex/学习笔记/Docker Compose 进阶
/Users/lyston/Obsidian/lyston/Codex/学习笔记/Kubernetes
/Users/lyston/Obsidian/lyston/Codex/学习笔记/数据库
```

For a new learning topic, create or update:

```text
/Users/lyston/Obsidian/lyston/Codex/学习笔记/<主题名>
```

These are conceptual study notes, so do not add device or environment suffixes unless the document is specifically about a machine, deployment, troubleshooting record, credential, or environment.

If the user provides an exact path, use that path. Otherwise, do not save teaching docs into the code workspace, `/tmp`, Downloads, or random scratch folders.

This skill itself is stored at:

```text
/Users/lyston/.codex/skills/teach-docs
```

## User's Required Teaching Style

The user wants a patient, detailed, step-by-step technical teaching style in Chinese. The goal is not a quick command cheat sheet. The document should teach the reader to understand, use, debug, and connect the topic to lower-level principles.

Use this style:

- 用中文写，像一个认真带学的老师，不要像百科词条。
- 先讲真实问题或使用场景，再讲概念，再讲命令或配置。
- 每个重要命令都要解释：这是什么、什么时候用、用在哪、解决什么问题、执行后应该看到什么。
- 每段配置都要解释关键字段，不要只贴 YAML、SQL、Shell。
- 要讲“为什么”，不只讲“怎么做”。
- 要把底层机制讲进去，但要融合到相关章节里，不要单独堆一个“底层原理大全”。
- 每章要有练习、观察命令、常见坑、检查点，让学习者知道自己是否真的懂了。
- 段落要短，推进要慢，一步一步搭台阶。
- 可以写得很详细，但细节必须服务于理解和实战，不要无关发散。
- 对比概念时用表格；讲流程时用简短步骤；讲心智模型时用 `text` 代码块。
- 保持“从小白能跟着练，到进阶能理解底层”的节奏。

Avoid this style:

- 只列命令，不解释命令背后的对象、场景和影响。
- 只新增一个章节讲原理，和原来的学习流程脱节。
- 把文档写成官方手册摘要、百科定义、零散知识点合集。
- 一上来堆大量术语，让读者不知道这些术语用在哪里。
- 为了显得高级而跳过安装、验证、排错和常见误区。

## Workflow

1. Save or update docs under `/Users/lyston/Obsidian/lyston/Codex/学习笔记` unless the user gives an exact path.
2. Read the existing document set before writing.
3. Identify the current section rhythm, paragraph length, command format, examples, and checkpoint style.
4. Apply the user's required teaching style above.
5. For large topics, split into a learning path and focused chapters. Do not put an entire course in one giant file.
6. For existing docs, update the smallest relevant chapters instead of creating duplicate summary files.
7. When the user asks for deeper understanding, integrate deeper mechanisms into the chapters where they explain real behavior.
8. Verify that each important command or config is explained by purpose, context, expected result, and common mistakes.

If writing into the user's Codex Obsidian Markdown space, use `codex-md-docs` for placement, naming, and update rules.

## How To Teach A Section

Prefer this structure inside each chapter:

```markdown
## Topic

Start with the real problem this topic solves.

Explain the concept in plain language.

Show the command or config.

Explain how to read every important line.

Connect it to the lower-level mechanism only where it helps.

Show how to observe or verify it.

Name common mistakes.

End with a short checkpoint.
```

Do not write a command block and assume the reader learned it. Every non-obvious command needs an answer to:

```text
What is this?
When do I use it?
What problem does it solve?
What happens underneath?
How do I know it worked?
What mistake would a beginner make here?
```

## Integrating Deeper Mechanisms

Do not add a standalone "underlying principles" chapter just because the user asks for depth.

Place mechanisms where they explain the current topic:

| Topic | Integrate mechanism where it belongs |
| --- | --- |
| Docker namespace / cgroup | Docker core concepts, resource limits, security, process isolation |
| Docker overlay2 / copy-on-write | Images, Dockerfile layers, volumes, persistence |
| Docker bridge / veth / NAT / DNS | Networking, port publishing, container communication, troubleshooting |
| Compose project / Docker API | Project model, final config, naming, lifecycle |
| Compose merge / env / profiles | Multi-environment config and `docker compose config` |
| Compose DNS / default bridge | Service-to-service communication and network debugging |
| Kubernetes reconciliation | Learning route, control plane, workloads, rollout, recovery |
| Kubernetes CRI / containerd / pause | Node, Pod, runtime model, container relationship |
| Kubernetes CNI / Service rules | Networking, DNS, Ingress, kube-proxy, eBPF/IPVS/iptables |
| Kubernetes CSI / PV / PVC | Storage, StatefulSet, cluster storage portability |
| Database B+Tree | Indexes, range queries, ordering, why functions can break index usage |
| Optimizer statistics | Execution plans, why an index may not be used |
| MVCC / locks | Transactions, isolation levels, read/write concurrency |
| WAL / binlog | Backup, recovery, replication, point-in-time recovery |

The mechanism should answer a practical question. If it does not change how the reader reasons, troubleshoots, or chooses a design, shorten it.

## Style Rules

- Use plain Chinese by default for this user's learning docs.
- Keep paragraphs short and progressive.
- Use concrete examples before abstractions.
- Prefer "why this exists" before "how to write it".
- Explain config line by line when the learner is likely to copy it.
- Use tables only when comparing choices.
- Use code fences for commands, YAML, SQL, config, logs, and mental models.
- Include commands to observe the system, not just commands to create things.
- Keep tone calm, practical, and encouraging.
- Avoid encyclopedia dumps, marketing prose, and unexplained jargon.

## Existing Document Updates

When improving existing teaching docs:

1. Do not change the teaching style unless requested.
2. Do not append all new depth at the end.
3. Do not create new "advanced", "bottom layer", "principles", or "summary" chapters unless the user asks.
4. Insert material beside the concept it clarifies.
5. Preserve headings, links, Obsidian wiki links, frontmatter, and unrelated content.
6. Keep edits scoped to the learning topic.
7. If the user complains the docs are shallow, add depth by explaining mechanisms, usage boundaries, debugging methods, and design tradeoffs inside the original flow.

## New Course Structure

For a large new learning path, use multiple files:

```text
00 学习路线与总览
01 核心概念
02 环境准备
03 基础操作
04 关键机制或常用场景
05 实战
06 排错
07 进阶与迁移
08 验收清单
```

Adjust names to the topic. The sequence should move from mental model to practice to troubleshooting.

Each chapter should stand alone enough to reopen later, but still fit the course path.

## Verification Checklist

Before saying the docs are done, check:

- Existing style was preserved.
- No giant one-file course was created for a broad topic.
- Deeper mechanisms were integrated into relevant chapters.
- Commands/configs explain purpose, context, and expected result.
- Reader can answer "what, why, when, how, how to verify".
- Troubleshooting and common mistakes are included where risk is high.
- No unrelated README, catalog, duplicate summary, or standalone theory file was created unless requested.
- Key terms requested by the user appear in the appropriate original chapters.

Useful local checks:

```bash
find <docs-dir> -maxdepth 1 -type f -name '*.md' | sort
rg -n 'keyword1|keyword2|keyword3' <docs-dir>
```

## Common Mistakes

| Mistake | Fix |
| --- | --- |
| Writing only commands | Add purpose, mechanism, expected output, and mistakes |
| Adding a separate theory dump | Move each mechanism into the chapter where it explains behavior |
| Rewriting the whole course voice | Match the existing style first |
| Over-teaching every detail | Teach depth only when it improves reasoning or troubleshooting |
| Hiding verification | Add observation commands and chapter checkpoints |
| Mixing unrelated topics | Split by learning path, but keep connected concepts linked |
