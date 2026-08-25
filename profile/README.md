# InfraZero

**JSX as the deployment language.**

Describe infrastructure and database schemas as components, render them to a plan, and deploy. Same mental model as a React tree — declarative, composable, diffable — applied to the things that usually live in YAML.

```tsx
/** @jsxImportSource @infra-x/runtime */
import { Host, Phase, File, SystemdService } from '@infra-x/host-library';

<Host address={process.env.SSH_HOST!} sshUser="deploy">
  <Phase type="setup">
    <File path="/etc/myapp/.env" content={process.env.APP_ENV_FILE!} />
    <SystemdService name="myapp" execStart="/usr/local/bin/myapp" />
  </Phase>
</Host>
```

That deploys an app to a VPS over SSH. The same JSX shape — different component libraries — targets Docker, Cloudflare Workers, Postgres schemas, and more.

🌐 **Site:** [infrazero.dev](https://infrazero.dev) · 𝕏 [@infrazerodev](https://x.com/infrazerodev)

> ### 🚧 Early alpha — not production ready
> Everything here is under active development, incompletely tested, and its APIs change without notice. Don't point it at production infrastructure or real data. Provided "AS IS", no warranty.

---

## 📦 Projects

<table>
  <tr>
    <td width="50%" valign="top">
      <a href="https://github.com/infra-zero/infrazero"><img src="https://img.shields.io/badge/infrazero-2dd4bf?style=for-the-badge&labelColor=1a1a1a" alt="infrazero" /></a>
      <p><strong>Infra-X</strong> — the runtime. JSX as the deployment language, plus reference component libraries for SSH hosts and Docker.</p>
      <a href="https://github.com/infra-zero/infrazero">Repo ↗</a>
    </td>
    <td width="50%" valign="top">
      <a href="https://github.com/infra-zero/infrazero-db"><img src="https://img.shields.io/badge/infrazero--db-10b981?style=for-the-badge&labelColor=1a1a1a" alt="infrazero-db" /></a>
      <p><strong>DB-X</strong> — database schema as JSX. Diff it, apply it, roll it back.</p>
      <a href="https://github.com/infra-zero/infrazero-db">Repo ↗</a> |
      <a href="https://infra-zero.github.io/infrazero-db/">Docs ↗</a>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <a href="https://github.com/infra-zero/examples"><img src="https://img.shields.io/badge/examples-94a3b8?style=for-the-badge&labelColor=1a1a1a" alt="examples" /></a>
      <p>Runnable example projects.</p>
      <a href="https://github.com/infra-zero/examples">Repo ↗</a>
    </td>
  </tr>
</table>

---

## 🛠️ Built with

TypeScript · Node.js · JSX · Cloudflare · Postgres · GitHub Actions · semantic-release

---

**Licensing:** BSL 1.1 for the core runtimes and CLIs, MIT for the component libraries — see `LICENSING.md` in `infrazero` and `infrazero-db`. The `examples` repo is MIT throughout.

💬 **Questions?** [Discussions on infrazero-db](https://github.com/infra-zero/infrazero-db/discussions) · ❤️ [Sponsor](https://github.com/sponsors/rtorcato)

Maintained by **[@rtorcato](https://github.com/rtorcato)** · [Matrix Digital Solutions](https://matrixdigital.com)
