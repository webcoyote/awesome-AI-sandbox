# Awesome AI Sandboxing

> A curated list of projects, tools, and references for running AI agents inside safer execution environments, with a focus on open-source solutions.

AI coding agents are useful precisely because they can read files, run commands, install packages, open network connections, and modify code. That also makes them risky. This list focuses on projects that reduce that risk with OS sandboxes, separate user accounts, virtual machines, containers, policy engines, and related guardrails.

## Contents

- [macOS-native sandboxes](#macos-native-sandboxes)
- [Virtual machines and disposable environments](#virtual-machines-and-disposable-environments)
- [Container and runtime sandboxes](#container-and-runtime-sandboxes)
- [Foundational sandbox tools](#foundational-sandbox-tools)
- [Permission and policy guardrails](#permission-and-policy-guardrails)
- [Deprecated and archived projects](#deprecated-and-archived-projects)
- [References](#references)

## macOS-native sandboxes

- [Agent Safehouse](https://github.com/eugene1g/agent-safehouse) - Deny-first macOS sandboxing for coding agents using composable `sandbox-exec` profiles, policy builder tooling, and audited profile fragments.
- [ClodPod](https://github.com/webcoyote/clodpod) - Runs AI agents inside a macOS VM while mapping one or more host project directories into the guest for isolated development.
- [SandVault](https://github.com/webcoyote/sandvault) - Runs Claude Code, OpenAI Codex, Gemini, and shell commands in a sandboxed macOS user account with a shared workspace and optional `sandbox-exec` hardening.
- [yoloAI](https://github.com/kstenerud/yoloai) - Sandboxed runner for AI coding agents that can use `sandbox-exec` on macOS, Tart on Apple Silicon, or Docker, with a review-and-apply workflow based on diffs and commits.
- [agent-sandbox.nix](https://github.com/archie-judd/agent-sandbox.nix) - Nix-based wrappers for sandboxing AI CLI tools with explicit package, state, and optional domain-level network allowances.
- [nixcage](https://github.com/hamidr/nixcage) - Sandboxed Nix environments with direnv auto-activation. Cross-platform: bwrap on Linux, sandbox-exec on macOS.

## Virtual machines and disposable environments

- [Chamber](https://github.com/cirruslabs/chamber) - Runs Claude or Codex inside ephemeral Tart macOS VMs with the current directory mounted, aimed at safer YOLO-mode agent execution.
- [Cleanroom](https://github.com/buildkite/cleanroom) - Self-hosted microVM sandbox for untrusted code with deny-by-default egress policy, repository-scoped allowlists, and host-side credential proxying.
- [ClodPod](https://github.com/webcoyote/clodpod) - macOS VM workflow for local Apple-platform development with Xcode and multiple mapped projects.
- [smolVM](https://github.com/smol-machines/smolvm) - Runs local microVMs for sandboxed workloads, with both ephemeral sandbox mode and persistent Linux VMs for isolated agent execution.
- [Sculptor](https://github.com/imbue-ai/sculptor) - Desktop app for running parallel Claude agents in isolated containers and pairing with their environments to test and merge changes.
- [yoloAI](https://github.com/kstenerud/yoloai) - Supports disposable Tart-backed sandboxes on macOS alongside other backends.
- [zapcode](https://github.com/TheUncharted/zapcode) - TypeScript interpreter for AI agents. Written in Rust. 2µs cold start. Sandboxed. Alternative to MCP tool calling.

## Container and runtime sandboxes

- [AIO Sandbox](https://github.com/agent-infra/sandbox) - All-in-one sandbox environment that combines browser, shell, file APIs, VS Code server, Jupyter, and MCP services in a single Docker container.
- [ClaudeBox](https://github.com/RchGrav/claudebox) - Docker-based Claude Code environment with per-project isolation, development profiles, persistent state, and firewall allowlists.
- [Kilntainers](https://github.com/Kiln-AI/Kilntainers) - MCP server that gives each agent an isolated ephemeral Linux sandbox backed by Docker, Podman, cloud microVMs, or WebAssembly.
- [sandbox-run](https://codeberg.org/Grauwolf/sandbox-run) - Lightweight `bubblewrap` wrapper for sandboxing development tools with per-project isolation for writes, temporary files, and session history.
- [sandclaude](https://github.com/binwiederhier/sandclaude) - Opinionated Docker wrapper for running Claude Code without restrictions inside a sandboxed container with mounted workspace and host-matched user IDs.
- [vibebin](https://github.com/jgbrwn/vibebin) - Incus/LXC-based platform for self-hosting persistent AI coding agent sandboxes on a Linux server with HTTPS routing, SSH access, and per-container tooling.
- [cco](https://github.com/nikvdp/cco) - Thin wrapper that launches Claude Code or Codex inside native OS sandboxes when available, with Docker as a stronger fallback barrier.
- [bunkervm](https://github.com/ashishgituser/bunkervm) - BunkerVM is a tiny operating system that boots in 2 seconds and gives AI agents a safe, isolated Linux machine to work in. Install it with one command. No Docker. No cloud. No config files.

## Foundational sandbox tools

- [bubblewrap](https://github.com/containers/bubblewrap) - Low-level Linux sandbox builder that creates restricted environments via namespaces and filesystem layout controls; used by higher-level tools to define their own security model.
- [Firejail](https://github.com/netblue30/firejail) - Lightweight Linux sandbox program using namespaces, seccomp-bpf, capabilities, and bundled profiles to restrict untrusted applications.
- [Minijail](https://github.com/google/minijail) - Sandboxing and containment tool used in ChromeOS and Android, providing both a launcher for sandboxed processes and a library for self-sandboxing.
- [syd](https://git.sr.ht/~alip/syd) - Linux application sandboxing tool that intercepts system calls in userspace and combines mechanisms like Landlock, namespaces, ptrace, and seccomp into a secure-by-default containment model.

## Permission and policy guardrails

- [Agent Safehouse](https://github.com/eugene1g/agent-safehouse) - Includes reusable least-privilege policy composition for running agents with fewer blanket permissions.
- [Cupcake](https://github.com/eqtylab/cupcake) - Policy enforcement layer for coding agents that evaluates hook events against OPA/Rego rules and can allow, modify, block, warn, or require review.
- [cco](https://github.com/nikvdp/cco) - Useful when the goal is to keep an agent in fast autonomous mode while interposing a sandbox boundary.
- [nah](https://github.com/manuelschipper/nah) - Context-aware Claude Code permission guard that classifies tool calls by action type and applies deterministic allow, ask, or block policies.
- [predicate-secure](https://github.com/PredicateSystems/predicate-secure) - Policy-based authorization wrapper for AI agents that adds pre-action guardrails, post-execution verification, and auditability across frameworks like Playwright, LangChain, and PydanticAI.
- [punkgo-jack](https://github.com/PunkGo/punkgo-jack) - Hook adapter for Claude Code and custom agents that records actions in an append-only Merkle log with cryptographic receipts and offline-verifiable session proofs.

## Deprecated and archived projects

- [Claude Code Sandbox](https://github.com/textcortex/claude-code-sandbox) - Archived Docker-based proof of concept for running Claude Code autonomously in isolated containers with a web UI and Git workflow integration.

## References

- [Awesome Sandbox](https://github.com/restyler/awesome-sandbox) - Broader survey of sandboxing technologies and platforms, including AI-oriented runtimes.
- [Hacker News discussion: Agent Safehouse](https://news.ycombinator.com/item?id=47301085) - Discussion that surfaced several current approaches to local agent isolation, including SandVault and yoloAI.
- [Hacker News discussion: Let's discuss sandbox isolation](https://news.ycombinator.com/item?id=47184049) - Practitioner discussion comparing user-account isolation, VMs, `bubblewrap`, and other models.
- [Hacker News thread 47343927](https://news.ycombinator.com/item?id=47343927) - Additional recent context on permission systems and the limits of coarse allow-or-deny prompts.

## Contributing

Suggestions and pull requests are welcome. Favor projects that are specifically about isolating, constraining, or safely operating AI agents, especially tools with a clear security model and practical documentation.
