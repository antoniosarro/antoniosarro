<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,100:f59e0b&height=200&section=header&text=Antonio%20Sarro&fontColor=ffffff&fontSize=60&fontAlignY=38&desc=dev%20%E2%80%A2%20homelab%20%E2%80%A2%20nix&descAlignY=60&descSize=18" width="100%" alt="Antonio Sarro" />

<div align="center">

<a href="https://antoniosarro.dev">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&pause=1000&color=F59E0B&center=true&vCenter=true&width=600&lines=Writing+Go+and+SvelteKit;NixOS+on+every+machine+%E2%9D%84%EF%B8%8F;Self-hosting+all+the+things+%F0%9F%8F%A0;Building+tools+for+local+LLMs+%F0%9F%A4%96" alt="Typing SVG" />
</a>

<br/>

[![Website](https://img.shields.io/badge/antoniosarro.dev-0d1117?style=flat-square&logo=googlechrome&logoColor=F59E0B)](https://antoniosarro.dev)
[![X](https://img.shields.io/badge/@antoniosarro-0d1117?style=flat-square&logo=x&logoColor=white)](https://x.com/antoniosarro)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0d1117?style=flat-square&logo=linkedin&logoColor=0A66C2)](https://linkedin.com/in/antoniosarro)
[![Hacker News](https://img.shields.io/badge/Hacker%20News-0d1117?style=flat-square&logo=ycombinator&logoColor=F0652F)](https://news.ycombinator.com/user?id=antoniosarro)
[![Email](https://img.shields.io/badge/Email-0d1117?style=flat-square&logo=protonmail&logoColor=6D4AFF)](mailto:contact@antoniosarro.dev)

</div>

<p align="center">
  <img src="assets/fetch.svg" alt="antonio@nixos fastfetch: NixOS, Hyprland, zsh, kitty, neovim, Talos homelab, Go and TypeScript" width="100%" />
</p>

### 🔨 Currently building

<div align="center">

<a href="https://github.com/antoniosarro/wisp">
  <img src="https://raw.githubusercontent.com/antoniosarro/wisp/main/assets/logo-dark.png" alt="wisp" width="120">
</a>

**[wisp](https://github.com/antoniosarro/wisp)**: a small, fast coding-agent harness for your terminal, built for local models.<br/>
Works with any OpenAI-compatible endpoint (llama.cpp, vLLM, Ollama, LM Studio, OpenRouter). It's a single static Go binary.

[![Release](https://img.shields.io/github/v/release/antoniosarro/wisp?style=flat-square&color=F59E0B&labelColor=0d1117)](https://github.com/antoniosarro/wisp/releases/latest)&nbsp;&nbsp;
[![Go](https://img.shields.io/badge/Go-0d1117?style=flat-square&logo=go&logoColor=00ADD8)](https://github.com/antoniosarro/wisp)

<a href="https://github.com/antoniosarro/wisp"><img src="https://raw.githubusercontent.com/antoniosarro/wisp/main/docs/images/chat.gif" alt="wisp answering a question about its own code" width="85%"></a>

</div>

### 🏠 Homelab

A bare-metal **Kubernetes** cluster on **Talos Linux**, run entirely through GitOps. I `git push`, and
**Flux** reconciles the cluster to match. No SSH, no clicking around, no snowflake servers.

<p>
  <img src="https://img.shields.io/badge/Talos-0d1117?style=flat-square&logo=talos&logoColor=FF7300" alt="Talos" />
  <img src="https://img.shields.io/badge/Kubernetes-0d1117?style=flat-square&logo=kubernetes&logoColor=326CE5" alt="Kubernetes" />
  <img src="https://img.shields.io/badge/Flux-0d1117?style=flat-square&logo=flux&logoColor=5468FF" alt="Flux" />
  <img src="https://img.shields.io/badge/Cilium-0d1117?style=flat-square&logo=cilium&logoColor=F8C517" alt="Cilium" />
  <img src="https://img.shields.io/badge/Longhorn-0d1117?style=flat-square&logo=longhorn&logoColor=5F224A" alt="Longhorn" />
  <img src="https://img.shields.io/badge/Helm-0d1117?style=flat-square&logo=helm&logoColor=0F1689" alt="Helm" />
  <img src="https://img.shields.io/badge/Let's%20Encrypt-0d1117?style=flat-square&logo=letsencrypt&logoColor=003A70" alt="Let's Encrypt" />
  <img src="https://img.shields.io/badge/OPNsense-0d1117?style=flat-square&logo=opnsense&logoColor=D94F00" alt="OPNsense" />
  <img src="https://img.shields.io/badge/Cloudflare-0d1117?style=flat-square&logo=cloudflare&logoColor=F38020" alt="Cloudflare" />
</p>


#### 🔁 How it works

```mermaid
flowchart LR
  dev["💻 git push"] --> fj["🦊 Forgejo<br/><i>in-cluster, source of truth</i>"]
  fj --> flux["🔁 Flux CD"]
  flux --> infra["⚙️ platform<br/>Cilium · Longhorn · cert-manager"]
  flux --> apps["📦 apps"]
  infra -.-> apps
  sops[("🔐 SOPS + age")] -.->|decrypts secrets| flux
```

#### 🖥️ The nodes

| Node | Hardware | Role |
| --- | --- | --- |
| 🔭 **orion** | i7-7700 · 32 GB · NVMe | workhorse: databases and heavy storage |
| 🎻 **lyra** | i5-6500 · 16 GB · SSD | general workloads *(joining soon)* |
| 🐦 **corvus** | Raspberry Pi 4 · 8 GB · arm64 | edge node *(joining soon)* |

#### ⚙️ The platform

| | |
| --- | --- |
| 🌐 **Networking** | Cilium with Gateway API in front of every app · Let's Encrypt wildcard TLS via cert-manager · OPNsense firewall with VLANs at the edge |
| 💾 **Storage** | Longhorn volumes replicated across the Intel nodes · nightly backups |
| 🔐 **Secrets** | Committed to git, encrypted with SOPS + age, decrypted in-cluster by Flux |
| 🧩 **New apps** | Scaffolded from a template with one `just` command, then validated before every push |

<details>
<summary><b>📦 What's running</b></summary>
<br/>

| | Services |
| --- | --- |
| 🛠️ **Dev** | Forgejo + CI runner |
| 🔐 **Security** | Vaultwarden |
| 🌐 **Network** | AdGuard Home · Caddy · Cloudflare DDNS |
| 📝 **Productivity** | AFFiNE · Memos · Linkding · Excalidraw · Homebox · Actual Budget · Stirling PDF · IT-Tools |
| 📊 **Dashboards & alerts** | Glance · Gotify |
| 🚀 **Web** | my personal site, self-hosted |

</details>

### ❄️ Nix everywhere

My desktop and laptop are built from **one NixOS flake**: the same modules, the same shell, the same
look, and every change is checked before it lands.

| | |
| --- | --- |
| 🖥️ **Machines** | Desktop (RTX 4070 Ti) and laptop, each on btrfs inside LUKS, partitioned declaratively with disko |
| 🧱 **Structure** | A `core` + `optional` split for both NixOS and home-manager: each host picks only the modules it needs. Hosts and custom packages are discovered automatically |
| 🪟 **Desktop** | Hyprland · Waybar · Rofi · greetd · kitty, with my own packaged Bibata Amber cursor |
| 🐚 **Shell** | zsh · starship · tmux · fzf · zoxide · eza · bat · lazygit · neovim, identical on every machine |
| 🔐 **Secrets** | sops-nix with age keys, so nothing sensitive is stored in plaintext |
| 🐳 **Virtualisation** | Docker · libvirt + virt-manager with TPM emulation · Waydroid |
| 🎮 **Gaming** | Steam with a gamescope session and gamemode |
| 🔭 **Astrophotography** | GraXpert, ASTAP and StarNet2, packaged myself because they aren't in nixpkgs |
| ✅ **Quality gates** | Eval checks, `nixfmt-rfc-style`, bats tests and pre-commit hooks, including private-key detection |

#### 🤖 Local AI stack

A **llama.cpp + llama-swap** backend serves a whole roster of models behind a single OpenAI-compatible
endpoint, hot-swapping whichever one is requested on 12 GB of VRAM:

- **Coding & homelab:** Qwen3.6-35B-A3B, a MoE model that runs at ~42 tok/s even with its weights offloaded to RAM
- **Writing & summaries:** Gemma 4 12B
- **Logs & structured work:** Granite 8B
- **Quick sub-agents:** small, fast 4B to 8B models for high-frequency loops

Each task gets its own agent role (homelab, NixOS, logs and more), all driven by
[wisp](https://github.com/antoniosarro/wisp).

### ✍️ Latest from the blog

<!-- BLOG-POST-LIST:START -->
- [Self-Hosted Container Management with Komodo: Your Own Deployment Platform in Docker](https://antoniosarro.dev/blog/komodo-homelab)
- [Self-Hosted Git with Forgejo: Your Own GitHub Alternative in Docker](https://antoniosarro.dev/blog/forgejo-homelab)
- [Building a High-Performance Portfolio with SvelteKit: A Deep Dive](https://antoniosarro.dev/blog/building-portfolio)
- [The Opinion Factory: When Everyone's Voice Becomes No One's Wisdom](https://antoniosarro.dev/blog/opinion-factory)
<!-- BLOG-POST-LIST:END -->

### 📈 Activity

<p align="center">
  <a href="https://git.io/streak-stats">
    <img src="https://streak-stats.demolab.com?user=antoniosarro&theme=github-dark-dimmed&hide_border=true&ring=F59E0B&fire=F59E0B&currStreakLabel=F59E0B" alt="GitHub Streak" />
  </a>
</p>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/antoniosarro/antoniosarro/output/snake-dark.svg">
  <img src="https://raw.githubusercontent.com/antoniosarro/antoniosarro/output/snake.svg" alt="Snake eating my contribution graph" width="100%">
</picture>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:f59e0b,100:0d1117&height=120&section=footer" width="100%" alt="" />
