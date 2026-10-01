---
# Indicator only: did the plugin actually dispatch its own agent? Kept
# out of the score with arm: with-only, because without the plugin the
# agent does not exist.
type: tool_used
tool: Agent
input_match: '"subagent_type"\s*:\s*"(?:gtm-planner:)?benchmark-researcher"'
arm: with-only
---
