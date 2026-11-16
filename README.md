# RateSonar plugins

RateSonar keeps a dated record of the interest rates Australian banks and lenders advertise.
This plugin adds RateSonar's read-only MCP server (`https://api.ratesonar.com`) and one skill
to your coding agent. No key and no sign-up.

## Claude Code

```
/plugin marketplace add jackfieldman/ratesonar-plugins
/plugin install ratesonar@ratesonar-plugins
```

## Codex

```
codex mcp add ratesonar --url https://api.ratesonar.com
```

The plugin also installs in Codex (`codex plugin marketplace add jackfieldman/ratesonar-plugins`,
then `codex plugin add ratesonar@ratesonar-plugins`) and adds the skill. In a local test on Codex
0.163 the plugin's MCP server did not start, so use the command above for the tools.

## What you get

- MCP server `ratesonar`: find_products, compare_rates, rate_history, rate_details, rate_changes,
  list_series, series, bank_position, bank_analysis, yield_curve, curve_pipeline_status.
- Skill `rate-lookup`: picks the tool and reports each rate with its recorded date.

Other apps (Claude, ChatGPT, Cursor, VS Code): https://ratesonar.com/agents/

Privacy: https://ratesonar.com/privacy/ · Terms: https://ratesonar.com/terms/
