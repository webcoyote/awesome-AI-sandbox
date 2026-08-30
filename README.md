# Awesome AI Sandboxing

> A curated list of projects, tools, and references for running AI agents inside safer execution environments, with a focus on open-source solutions.

AI coding agents are useful precisely because they can read files, run commands, install packages, open network connections, and modify code. That also makes them risky. This list focuses on projects that reduce that risk with OS sandboxes, separate user accounts, virtual machines, containers, policy engines, and related guardrails.

## Contents

- [Host-level sandboxes and local workspace isolation](#host-level-sandboxes-and-local-workspace-isolation)
- [Virtual machines and microVM platforms](#virtual-machines-and-microvm-platforms)
- [Containers, LXC, and packaged runtimes](#containers-lxc-and-packaged-runtimes)
- [Policy, approvals, and audit layers](#policy-approvals-and-audit-layers)
- [Foundational sandbox primitives and low-level tooling](#foundational-sandbox-primitives-and-low-level-tooling)
- [Profiles, templates, and operational helpers](#profiles-templates-and-operational-helpers)
- [Adjacent agent systems and specialized experiments](#adjacent-agent-systems-and-specialized-experiments)
- [References](#references)

## Host-level sandboxes and local workspace isolation

### Multiplatform

- [cage](https://github.com/pacificsky/cage) - Cage runs coding agents in isolated Docker containers on macOS or Linux
- [agent-sandbox.nix](https://github.com/archie-judd/agent-sandbox.nix) - Nix wrappers for constrained AI CLI execution with explicit package and network allowances.
- [cco](https://github.com/nikvdp/cco) - Thin launcher that picks a local sandbox backend rather than implementing one from scratch.
- [nixcage](https://github.com/hamidr/nixcage) - Nix environment sandboxing with `bubblewrap` on Linux and `sandbox-exec` on macOS.
- [Pent](https://github.com/valentinradu/pent) - Native OS process sandbox for untrusted commands.
- [Sandbox Runtime](https://github.com/anthropic-experimental/sandbox-runtime) - OS-level filesystem and network restriction layer without containers.
- [sandnix](https://github.com/srid/sandnix) - Nix module for wrapping programs with Landlock or `sandbox-exec`.
- [workmux](https://github.com/raine/workmux) - Git worktree and `tmux` workflow isolation; useful alongside a real sandbox, but not a full security boundary by itself.
- [yoloAI](https://github.com/kstenerud/yoloai) - Multi-backend local runner that can use macOS Seatbelt, Tart, or Docker with review/apply workflow.

### macOS

- [Agent Safehouse](https://github.com/eugene1g/agent-safehouse) - Deny-first macOS Seatbelt profile system for local coding agents.
- [sandbox-shell](https://github.com/agentic-dev3o/sandbox-shell) - macOS Seatbelt shell wrapper for deny-by-default filesystem access.
- [SandVault](https://github.com/webcoyote/sandvault) - Runs agents in a separate macOS user account with `sandbox-exec` hardening.
- [vibebox](https://github.com/robcholz/vibebox) - Fast local macOS sandbox oriented toward AI-agent use.
- [yolobox](https://github.com/finbarr/yolobox) - Local sandbox focused on letting agents work without exposing the full home directory.

### Linux

- [sandlock](https://github.com/multikernel/sandlock) - Confines untrusted code using Landlock, seccomp-bpf, and seccomp user notification.
- [Fence](https://github.com/use-tusk/fence) - Native command sandbox for filesystem and network restrictions without containers.
- [Matchlock](https://github.com/jingkaihe/matchlock) - Linux sandbox aimed at securing AI agent workloads.
- [Microbox](https://github.com/hqarroum/microbox) - Lightweight ephemeral Linux sandboxes.
- [Nono](https://github.com/always-further/nono) - Capability-oriented kernel-backed sandbox for agent execution.
- [sandbox-run](https://codeberg.org/Grauwolf/sandbox-run) - `bubblewrap`-based wrapper for per-project Linux command isolation.
- [sandbox-runtime](https://github.com/carderne/sandbox-runtime) - Lightweight process sandbox for filesystem and network policy enforcement.
- [shai](https://github.com/colony-2/shai) - Sandboxing shell for AI coding agents.
- [sucoder](https://github.com/ligon/sucoder) - Unix-permissions-based approach for containing coding agents.
- [treebeard](https://github.com/divmain/treebeard) - Ephemeral Git worktree sandbox with copy-on-write handling and optional network restrictions.

## Virtual machines and microVM platforms

### Multiplatform

- [boxed](https://github.com/akshayaggarwal99/boxed) - Code-execution engine for untrusted agent code across Docker, Firecracker, and Wasm.
- [boxlite-labs/boxlite](https://github.com/boxlite-labs/boxlite) - Closely related BoxLite implementation under a different org namespace.
- [BoxLite](https://github.com/boxlite-ai/boxlite) - Embeddable VM-style sandboxing with snapshots and persistent state.
- [coderunner](https://github.com/instavm/coderunner) - Hosted-style sandbox runner for untrusted AI code.
- [K7](https://github.com/katakate/k7) - Self-hosted lightweight VM sandbox infrastructure with API and SDK support.
- [smolVM](https://github.com/smol-machines/smolvm) - Local microVM manager for ephemeral and persistent isolated workloads.

### macOS

- [Chamber](https://github.com/cirruslabs/chamber) - Ephemeral Tart-based macOS VM runner for Claude or Codex.
- [ClodPod](https://github.com/webcoyote/clodpod) - macOS VM workflow that maps host projects into a guest environment.
- [lima-devbox](https://github.com/recodelabs/lima-devbox) - Lima-based VM dev sandbox workflow for Mac.

### Linux

- [agentsafe](https://github.com/sarthak30/agentsafe) - Per-task microVM sandbox for AI agents.
- [avkcode/firecracker-sandbox](https://github.com/avkcode/firecracker-sandbox) - Firecracker-based sandbox experiment.
- [bunkervm](https://github.com/ashishgituser/bunkervm) - Tiny Linux VM environment positioned as a simple safe machine for agents.
- [Cleanroom](https://github.com/buildkite/cleanroom) - Self-hosted microVM sandbox with deny-by-default egress and credential proxying.
- [hhtpcd/firecracker-sandbox](https://github.com/hhtpcd/firecracker-sandbox) - Another Firecracker sandbox implementation.
- [nervos](https://github.com/ashishgituser/nervos) - Firecracker-microVM sandbox for AI agents.
- [python-firecracker](https://github.com/okeso/python-firecracker) - Python interface for Firecracker rather than a full agent sandbox product.

## Containers, LXC, and packaged runtimes

### Multiplatform

- [agentbox](https://github.com/gbrindisi/agentbox) - Containerized agent sandbox with network firewalling and privilege dropping.
- [AIO Sandbox](https://github.com/agent-infra/sandbox) - Full-featured Docker sandbox with shell, browser, files, Jupyter, VS Code server, and MCP.
- [Amazing Sandbox](https://github.com/ashishb/amazing-sandbox) - General local sandbox for third-party tools and AI agents.
- [claude-code-devcontainer](https://github.com/trailofbits/claude-code-devcontainer) - Hardened devcontainer template rather than a new sandbox primitive.
- [ClaudeBox](https://github.com/RchGrav/claudebox) - Docker-based Claude Code environment with persistent state and allowlists.
- [codex-lockbox](https://github.com/paulux84/codex-lockbox) - Docker sandbox focused on running Codex CLI behind firewall rules.
- [conch](https://github.com/sd2k/conch) - Wasm/bash-style sandbox approach for agent command execution.
- [EdgeBox](https://github.com/bigppwong/edgebox) - Local GUI sandbox that exposes a desktop to the agent.
- [Kilntainers](https://github.com/Kiln-AI/Kilntainers) - MCP-oriented sandbox runtime backed by Docker, Podman, microVMs, or Wasm.
- [packnplay](https://github.com/obra/packnplay) - Docker-backed command sandbox with worktree and dev-container management.
- [sandclaude](https://github.com/binwiederhier/sandclaude) - Opinionated Docker wrapper for Claude Code.
- [Sculptor](https://github.com/imbue-ai/sculptor) - Desktop tooling for running agents inside isolated containers and testing changes.

### Linux

- [Greywall](https://github.com/greyhavenhq/greywall) - Local sandbox with live network-control and visibility features.
- [runbox](https://github.com/sahilb315/runbox) - Minimal container-like sandbox implementation in C.
- [sbox](https://github.com/cvpaul/sbox) - Small isolation-first sandbox project.
- [vibebin](https://github.com/jgbrwn/vibebin) - Incus/LXC platform for persistent self-hosted coding-agent sandboxes.

## Policy, approvals, and audit layers

### Multiplatform

- [claude-rule-enforcer](https://github.com/tech-and-ai/claude-rule-enforcer) - Restriction and rules enforcement around Claude Code behavior.
- [Cupcake](https://github.com/eqtylab/cupcake) - OPA/Rego-based hook enforcement for coding agents.
- [deepclause-sdk](https://github.com/deepclause/deepclause-sdk) - Policy/runtime SDK for DML-style authorization logic.
- [nah](https://github.com/manuelschipper/nah) - Deterministic allow/ask/block guard for Claude Code tool calls.
- [predicate-secure](https://github.com/PredicateSystems/predicate-secure) - Policy-based authorization and post-run verification for agents.
- [punkgo-jack](https://github.com/PunkGo/punkgo-jack) - Audit and receipt layer for agent actions via Merkle-logged hook events.
- [shannot](https://github.com/corv89/shannot) - Human-in-the-loop execution and approval flow for LLM agents.
- [SandBase Harness](https://github.com/sandbaseai/sandbase-harness) - Local-first agent runtime with governed tool access, credential management, approval workflows, sandboxed sessions, and audit/replay.

### Linux

- [firewarden](https://github.com/pigmonkey/firewarden) - Opens files inside private Firejail sandboxes; more policy wrapper than agent runtime.

## Foundational sandbox primitives and low-level tooling

### Multiplatform

- [agentfs](https://github.com/tursodatabase/agentfs) - Agent-oriented filesystem layer, useful as a constrained I/O substrate rather than a complete sandbox.

### Linux

- [bubblewrap](https://github.com/containers/bubblewrap) - Core Linux namespace/filesystem sandbox builder.
- [bVisor](https://github.com/butter-dot-dev/bvisor) - Embedded bash sandbox inspired by gVisor.
- [firecracker-go-sdk](https://github.com/firecracker-microvm/firecracker-go-sdk) - Go SDK for assembling Firecracker-backed runtimes.
- [Firejail](https://github.com/netblue30/firejail) - Mature Linux desktop/application sandbox using namespaces and seccomp.
- [gVisor](https://github.com/google/gvisor) - User-space kernel / application-kernel boundary used to harden containerized execution.
- [island](https://github.com/landlock-lsm/island) - Landlock-powered Linux sandbox CLI.
- [libkrun](https://github.com/containers/libkrun) - Lightweight virtualization runtime frequently used under higher-level sandbox systems.
- [Minijail](https://github.com/google/minijail) - ChromeOS/Android containment launcher and library.
- [sacre_bleu](https://github.com/hsaliak/sacre_bleu) - Seccomp and Landlock policy generation, injection, and enforcement suite for Linux binaries.
- [syd](https://git.sr.ht/~alip/syd) - Userspace syscall-intercepting Linux sandbox.

## Profiles, templates, and operational helpers

### Linux

- [ansible-firejail](https://github.com/debops-contrib/ansible-firejail) - Ansible automation for deploying Firejail profiles.
- [bubblewrap-tui](https://github.com/reubenfirmin/bubblewrap-tui) - Terminal UI for constructing Bubblewrap command lines.
- [firejail-profiles](https://github.com/chiraag-nataraj/firejail-profiles) - Profile collection for Firejail-based sandbox setups.
- [firetools](https://github.com/netblue30/firetools) - GUI companion for working with Firejail sandboxes.

## Adjacent agent systems and specialized experiments

### Multiplatform

- [ash-ai](https://github.com/ash-ai-org/ash-ai) - Hosted agent infrastructure that includes sandboxing among broader API/session concerns.
- [bouvet](https://github.com/vrn21/bouvet) - Rust agent sandbox project; promising, but closer to an early experiment than a mature platform.
- [cagent](https://github.com/noperator/cagent) - Related repository mentioned in sandbox-isolation discussion; not clearly positioned as a general-purpose sandbox product.
- [co-do](https://github.com/paulkinlan/co-do) - Browser-as-sandbox experiment, useful conceptually but narrower than a general local sandbox.
- [construct-cli](https://github.com/estebanforge/construct-cli) - Secure loading/execution project for AI agents.
- [forgemax](https://github.com/postrv/forgemax) - MCP gateway with sandboxed code execution for tool orchestration.
- [litterbox](https://github.com/gerharddc/litterbox) - Deep-dive repository about agent sandboxes; more analysis than runtime.
- [microsandbox](https://github.com/zerocore-ai/microsandbox) - Sandbox-focused exploration rather than a clearly defined end-user runtime.
- [OmniGlass](https://github.com/goshtasb/omniglass) - Sandboxed visual action engine, more specialized than a general code-execution sandbox.
- [qonqrete](https://github.com/illdynamics/qonqrete) - Local-first multi-agent code-generation system with sandbox claims.
- [rcarmo/agentbox](https://github.com/rcarmo/agentbox) - Notes and operational writeup about a personal sandboxing setup, not a standalone runtime.
- [selenai](https://github.com/almclean/selenai) - Terminal pair-programming agent with sandboxed Lua tools.
- [SkillSandbox](https://github.com/themachineclay/skillsandbox) - Capability-oriented runtime for agent skills rather than a general process/container boundary.
- [smith-core](https://github.com/sibyllinesoft/smith-core) - Secure personal-agent platform combining sandboxing, policy, and observability.
- [tsk](https://github.com/dtormoen/tsk) - Delegation and parallelization tool with sandbox positioning.
- [voratiq](https://github.com/voratiq/voratiq) - Agent-ensemble coding system; sandboxing is secondary to orchestration.
- [VTCode](https://github.com/vinhnx/vtcode) - Coding agent with strong shell-safety posture, but not primarily a sandbox runtime.
- [YourOwnPersonalJean-Luc](https://github.com/waynecider/yourownpersonaljean-luc) - Local coding agent with defense-in-depth positioning.
- [zapcode](https://github.com/TheUncharted/zapcode) - Sandboxed TypeScript execution engine for AI tools, closer to a specialized runtime than a full workstation sandbox.

## References

- [Awesome Agent Sandboxes](https://github.com/arjan/awesome-agent-sandboxes) - Curated list focused on AI/LLM execution sandboxes.
- [Awesome Sandbox](https://github.com/restyler/awesome-sandbox) - Broad survey of sandboxing technologies and platforms.
- [Hacker News discussion: Agent Safehouse](https://news.ycombinator.com/item?id=47301085) - Discussion of recent local agent-isolation approaches.
- [Hacker News discussion: Let's discuss sandbox isolation](https://news.ycombinator.com/item?id=47184049) - Practitioner thread comparing user accounts, VMs, `bubblewrap`, and related approaches.
- [Hacker News thread 47343927](https://news.ycombinator.com/item?id=47343927) - Additional discussion on permissions and coarse-grained approval models.

## Contributing

Suggestions and pull requests are welcome. Favor projects that are specifically about isolating, constraining, or safely operating AI agents, especially tools with a clear security model and practical documentation.
