# 👻 Ghost Agent Tools ⭐

A skill for managing [Ghost](https://ghost.org) blogs from Codex, Claude Code, and other agents that support [Agent Skills](https://agentskills.io).

## Plugins

### ghost-blog

Create, update, publish, and schedule posts, upload images, and manage tags, members, and newsletters.

Uses Ghost's Content API (read-only) and Admin API (read/write) with a Python client that uses only the standard library. The Markdown helper uses `markdown` and `markdownify`, installed automatically by [uv](https://docs.astral.sh/uv/).

## Installation

Install [uv](https://docs.astral.sh/uv/getting-started/installation/), then choose one installation method to avoid duplicate skills. All methods use the same `ghost-blog` skill and Python helpers.

### Skills CLI

Install with the [Skills CLI](https://skills.sh/) for Codex, Claude Code, and other supported agents:

```bash
npx skills add georgeguimaraes/ghost-agent-tools
```

Start a new session after installation.

### Claude Code

```text
/plugin marketplace add georgeguimaraes/ghost-agent-tools
/plugin install ghost-blog@ghost-agent-tools
```

### Codex

```bash
codex plugin marketplace add georgeguimaraes/ghost-agent-tools
codex plugin add ghost-blog@ghost-agent-tools
```

To try a local checkout, use its absolute path in the first command instead of the GitHub repository. Start a new session after installation.

### Standalone skill

For Codex and other agents that discover skills in `~/.agents/skills`, clone into a persistent location and link the skill folder:

```bash
git clone https://github.com/georgeguimaraes/ghost-agent-tools.git "$HOME/.local/share/ghost-agent-tools"
mkdir -p "$HOME/.agents/skills"
ln -s "$HOME/.local/share/ghost-agent-tools/plugins/ghost-blog/skills/ghost-blog" "$HOME/.agents/skills/ghost-blog"
```

If the destination already exists, inspect it before replacing it. Updating the clone updates the linked skill. Start a new session after installation.

For agents with a different skill directory, install the complete `plugins/ghost-blog/skills/ghost-blog/` folder there, including both Python helpers.

Previously named `claude-code-ghost`. If you installed the old marketplace, uninstall `ghost-blog` from it, remove that marketplace, then add `ghost-agent-tools` using the commands above. The plugin and skill are still named `ghost-blog`.

## Configuration

Create a Custom Integration in your Ghost Admin (Settings > Integrations). Set these variables in the environment where your agent runs helper commands:

```bash
export GHOST_API_URL="https://yourblog.ghost.io"
export GHOST_CONTENT_API_KEY="your-content-api-key"
export GHOST_ADMIN_API_KEY="your-admin-api-key-id:secret"
```

The Content API key is needed for public reads. The Admin API key is needed for drafts and writes.

## Usage

Ask your agent to interact with your blog. In Codex, select the skill with `/skills`, or invoke `$ghost-blog` for a standalone installation and `$ghost-blog:ghost-blog` for the plugin:

- "list my recent blog posts"
- "create a draft about topic X"
- "publish my draft"
- "schedule a post for tomorrow at 9am"
- "upload this image to my blog"
- "show me my blog tags"
- "filter posts by tag"

## License

MIT
