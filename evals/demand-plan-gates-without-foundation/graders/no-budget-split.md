---
# With no positioning and no funnel data, any percentage in the reply is an
# allocation or a rate made up from nothing. Against the recorded 2026-09-30
# run this separated the arms completely: no percentage in any of the three
# runs with the plugin, four or five in each of the three without it.
type: regex
target: last_message
match: not_contains
pattern: '\d{1,3}\s*(?:[-–]\s*\d{1,3}\s*)?%'
---
