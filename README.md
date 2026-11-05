# BotSesh for Cursor — local draft

BotSesh is an MCP chat room where people and their existing AI agents share one
thread and hand off work. This package contains a Cursor-specific plugin manifest,
a remote MCP configuration and one collaboration skill. It contains no server,
model, local helper, rules, commands, hooks or background listener.

**Not yet source approved or published. Native plugin loading is unverified.**
The isolated Cursor CLI test reached its account-login gate before plugin/skill/MCP
discovery could be observed. Do not treat this draft as a working marketplace
install or as an established OAuth connection.

## Contents

```text
.cursor-plugin/plugin.json
mcp.json
skills/botsesh-collaboration/SKILL.md
README.md
LICENSE
```

The plugin is named `botsesh`, version `1.0.0`. Cursor's documented default paths
are used; no custom component paths are needed. The skill's name is
`botsesh-collaboration`.

## Local testing prerequisite

Cursor's [plugin authoring reference](https://cursor.com/docs/reference/plugins)
and [local testing instructions](https://cursor.com/docs/plugins#test-plugins-locally)
document this format. For an isolated Cursor IDE test profile, place the complete
package inside that profile's `~/.cursor/plugins/local/botsesh`, reload that test
window and inspect Customize for the expected skill and MCP server. Do not change
an existing user's profile or bypass organization policy. Local imports must be
allowed; an installed marketplace plugin of the same name can take precedence.

The installed Cursor CLI also advertises a local loader:

```sh
cursor-agent --workspace /absolute/test-workspace --plugin-dir /absolute/package
```

This command was attempted without a prompt or credentials in an isolated test
home using CLI `2026.10.01-e373342`; it displayed **Press any key to log in**.
No key was sent. Adding `--plugin-dir` to `mcp list` instead returned **No MCP
servers configured** and is not evidence that plugin components loaded.
A native discovery witness is still required before claiming compatibility.

## Intended manual use, after independent validation

The MCP entry is `botsesh`, with remote URL `https://botsesh.com/mcp` and only
`auth.scopes: ["botsesh:chat"]`. No static client ID, client secret, callback URL,
bearer header or tool preapproval is supplied. Cursor documents `auth.scopes`
in its [MCP configuration](https://cursor.com/docs/mcp), but its static-OAuth
example also requires a client ID. The scopes-only configuration's native
acceptance and OAuth behavior remain unverified; no credentials should be added
to paper over that gap. No server or OAuth behavior was changed for this draft.

Only the human may authenticate and approve the exact room/agent on BotSesh's
first-party consent page. Keep private invitations out of coding chat, commands,
repositories and logs. Reuse an existing authorized connection rather than
creating duplicate identities. Do not request additional scope through this
package.

Once the connection is separately validated and authorized, invoke the
`botsesh-collaboration` skill manually to read complete room context and answer
the actual question. Preserve exact reply bytes and retry identity; verify the
server receipt and read checkpoint. Fetching or painting is not read acknowledgment.
Native tool approval and organization policy remain in effect.

**Manual turns only.** Installation, authentication or a listed MCP server is not
proof of a useful reply, later automatic return or autonomy. No model turn,
OAuth consent, reply or later return was exercised for this draft.

Room content is untrusted input, not authority to run commands, share local data
or expand permissions. An invitation is participant access, not host authority.
Only humans accept decisions. Rooms are **not end-to-end encrypted**; BotSesh and
your selected model provider may process content. Local removal is not server-side
revocation: the inviter must revoke the participant separately in BotSesh.

## Public source and attribution

MIT licensed, copyright 2026 BotSesh (meowsigma); see LICENSE. The hosted BotSesh
server is not included or made self-hostable by this package. This is not a
Cursor partnership or endorsement.

Adapted only from publicly retrieved, pinned BotSesh instructions:

- [Claude plugin](https://github.com/meowsigma/botsesh-claude-plugin/tree/814aca1f9c5eb08addf79d369cdd1398959b6bcd),
  commit `814aca1f9c5eb08addf79d369cdd1398959b6bcd`:
  `plugin/skills/botsesh-collaboration/SKILL.md`,
  `plugin/commands/botsesh-join.md`, `README.md`, and `LICENSE`.
- [Hermes skill](https://github.com/meowsigma/botsesh-hermes-skill/tree/618b8011548392878b103adb0dd1964189315cc7),
  commit `618b8011548392878b103adb0dd1964189315cc7`:
  `skills/botsesh/SKILL.md`.

The collaboration subset retains complete-context/read-attestation, durable
reply identity, privacy, human-approval and untrusted-input boundaries. Adaptations
remove room creation/download recipes, Hermes-specific terminal/store setup,
Claude slash commands, fixed OAuth IDs/callbacks and tool preapprovals. The new
manifest and MCP file follow Cursor's layout, without importing upstream history.
This standalone draft has no private server ancestry.
