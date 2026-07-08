A folder containing Skill file

name
description
INsructions

Conventions:
fileName: SKILL.md
folderName: client-monthly-summary
format:

---

name: client-monthly-summary
description: Prepares a monthly client financial summary for an
accounting firm. Use when the user asks for a "client summary",
"monthly close", or "month-end report". Formats amounts in the
firm's reporting currency, groups by expense head, and flags
tax-withholding items.

---

# Instructions

When asked to prepare a client summary or monthly close:

1. Format every amount in the reporting currency above, with thousands
   separators (e.g., "1,250,000").
2. Group all line items by expense head. Sort heads by total,
   largest first.
3. Flag any single payment above the withholding threshold above
   with a "⚑ WITHHOLDING" note.
4. Produce the report in exactly four sections, in this order:
   Overview, Income, Expenses by Head, Flags & Notes.

references/
assets/
scripts/

(3 folders lazily loaded when needed)

Description: what it does + when to use it + the exact phrases you'd actually say.
Example:
"Converts consultation notes into SOAP-format clinical notes.
Use when the user asks for a 'SOAP note',
'clinical note', or to 'write up' a consultation."

A handy debugging trick once a skill is installed:
ask AI, "When would you use my client-summary skill?"
It will paraphrase the description back to you.
If its answer is narrower or wider than you intended,
you've found exactly what to fix in the description.

You can also add negative triggers when a skill fires too eagerly: "Do NOT use for one-off calculations or quick questions — only for full month-end reports."

---

Skill Buildig

Phase 1 : Drafting the Skill

1. Describe the skill and let AI generate the first version.
2. Read it and fix anything obviously wrong before testing.

Phase 2 : Test Triggering
3)Test triggering. Try the phrases that should activate it ("prepare the client summary," "do the monthly close," "write up the month-end report") and confirm it loads. Try unrelated requests and confirm it does not take over ones it shouldn't.

Two failure patterns and their fixes:

It never triggers → the description is too vague or missing the words you actually use. Add them.
It triggers on the wrong things → the description is too broad. Narrow it, or add a negative trigger.

Phase 3 : Test the output

4)Test the output. Run the skill on a real (or realistic) input. Does it format in the right currency? Group by head? Flag withholding? Hit all four sections?

5)Test it with hard cases. A client with no income that month. A payment exactly on the threshold. A messy ledger. Where it fails, make the instructions more precise, and consider whether a tricky calculation should be a small script instead of a prose instruction, because code is exact and prose is interpreted.

Phase 4 : Update the Skill

6)Bring failures back to skill-creator: "This skill double-counted reversed entries. Update it to net out reversals before grouping."

---

Skill Building:

Use the skill-creator skill to help me build a skill.

The skill prepares a monthly client financial summary for my
accounting firm. Whenever I ask for a "client summary"
or "monthly close," it should:

- Format all amounts in our reporting currency with thousands separators.
- Group line items by expense head.
- Flag any payment above the tax-withholding reporting threshold.
- Output using my standard four-section report layout
  (Overview, Income, Expenses by Head, Flags & Notes).

Ask me anything you need, then build it.

---

Permissions:
The principle is identical everywhere: you grant access, AI inherits your permissions, you start read-only.

3 steps:

1.Grant access: You choose which tools (files, email, apps) the AI can reach. This is like giving the AI a key ring to your workspace.
2.AI inherits permissions: The AI doesn’t get new privileges of its own; it uses the same rights you’ve assigned. If you can view something, the AI can view it; if you can edit something, the AI can edit only if you allowed write access.
3.Start read-only: By default, the AI begins with read-only access. It can only look at data and patterns, not change anything, until you explicitly raise its permissions (e.g., grant write access or allow specific actions).

Read a skill before enabling it; scope a connector before trusting it.

A skill is a set of instructions you are letting AI follow, and a connector is a door into your real data. Treat a skill from a stranger like a contract you're about to sign, and a connector like a key you're about to hand over.

---

# Skill Creator Template

Use the skill-creator skill to help me build a skill.

The skill prepares a monthly client financial summary for my
accounting firm. Whenever I ask for a "client summary"
or "monthly close," it should:

- Format all amounts in our reporting currency with thousands separators.
- Group line items by expense head.
- Flag any payment above the tax-withholding reporting threshold.
- Output using my standard four-section report layout
  (Overview, Income, Expenses by Head, Flags & Notes).

Ask me anything you need, then build it.

# Description Checklist

## Triggers [Mandatory]

List all reasonable ways a user might ask for the capability, including explicit requests, implicit requests, common synonyms, and natural language variations.

## Scope [Mandatory]

Define which requests the skill should and should not handle.

Include two sections:

Eligible Requests — Requests that match the intended workflow.
Not Eligible Requests — Requests that fall outside the skill's purpose.

## Full Workflow vs. Direct Answer [Only if the skill has a meaningful partial request scenario]

Determine whether the user wants the complete workflow or only a specific part of it.

If the user requests the complete workflow, trigger the skill.
If the user requests only a specific section or a simple answer, respond directly without triggering the skill.

## Clarify Before Proceeding [Mandatory]

If multiple interpretations are possible, clarify the user's intent before starting the workflow. Don't guess what the user wants. Ask a clarifying question whenever the request is ambiguous. Handle unclear requests with a clarifying question.

## Confirmation Checkpoint [Mandatory]

Before executing the workflow, explicitly tell the user what will be executed and ask for confirmation.

This is the final checkpoint after all other conditions have been satisfied.

## Negative Trigger [Strongly recommended, but if the scope is already very precise and there are few adjacent intents, a separate section may not add much.]

List explicit exclusions—requests that should never trigger the skill, even if they appear related.
Explicit exclusions. It improves precision. Invest here not in just Synonyms. People underinvest here.

---

Use /skill-creator to help me build a skill.

The skill evaluates the trigger description of another skill using the framework below.Evaluate only the skill's description and trigger behavior. Do not evaluate the skill's implementation, output quality, or workflow.

. Whenever I ask for a "description evaluation" or "skill description evaluation," it should evaluate the description based on following criteria however Handle unclear requests with a clarifying question and confirm with user before execution always:

````



Triggers  [Mandatory] - List all reasonable ways a user might ask for the capability, including explicit requests, implicit requests, common synonyms, and natural language variations.



Scope [Mandatory] - Define which requests the skill should and should not handle. Include two sections : Eligible Requests — Requests that match the intended workflow. Not Eligible Requests — Requests that fall outside the skill's purpose.



Full Workflow vs. Direct Answer [Only if the skill has a meaningful partial request scenario] - Determine whether the user wants the complete workflow or only a specific part of it. If the user requests the complete workflow, trigger the skill. If the user requests only a specific section or a simple answer, respond directly without triggering the skill.



Clarify Before Proceeding [Mandatory] - If multiple interpretations are possible, clarify the user's intent before starting the workflow. Don't guess what the user wants. Ask a clarifying question whenever the request is ambiguous. Handle unclear requests with a clarifying question.



Confirmation Checkpoint [Mandatory] -  Before executing the workflow, explicitly tell the user what will be executed and ask for confirmation. This step should occur only after all previous checks have passed.



Negative Trigger [Strongly recommended, but if the scope is already very precise and there are few adjacent intents, a separate section may not add much.] - List explicit exclusions—requests that should never trigger the skill, even if they appear related. Explicit exclusions. It improves precision. Invest here not in just Synonyms. People underinvest here.  ```

````

---

Formula For Skill Description and Triggering:

1. Trigger only for explicit or implicit requests for [capability].
2. Never trigger for [explicit exclusions].
3. Proceed only if request is within [scope].

Formula for Instructions:

1. Answer partial requests directly; only trigger for full workflows.
2. Ask a clarifying question if the request is ambiguous.
3. Confirm with the user before executing the workflow.

Description = Triggers + Negative Trigeers + Scope
Skill Body = Partial Requests Behaviour + Instructions for Full Request + Clarification Question + Confirm with user
