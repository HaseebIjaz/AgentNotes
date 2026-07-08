Claude Code/Open Code kay basic kamm:
1.Model Set karna -> /model or /models [Configure Model Providers along] [For Open Code -> DeepSeek and GLM]
2.Model Selection [Know which models to use for which Task] [Model Selection according to Task] 3. Koi bhi kamm karnay sayy pehlay Plan banwayein , Koi bhi kamm karnay sayy pehlay plan banwayein . Always ask for Plan
[AI Works better with Plan]
4.Read the plan, Edit the Plan.
5.Permission Discipline
a) Set the Scope to the desired folder.
b) Auto approve safe actions which are readonly and about running tests [Auto Approve Readonly]
c)It will ask for your confirmation before doing anything. Reject if it doesnt look right to you.

For Example : Agar mene koi app banwani haii too direct nai Prompt likh dunn gaa, iss kii bajaye iss sayy plan likhwaon gaa

Checkable Task
Dont rely on stealth mode models

Know your models, which one you would be using, their provider, their data policy aand pricing

--> Check current Model
--> List all Models
--> Switch Models

## KNOW YOUR MODEL

claude update
opencode upgrade

---

Different model for planning and different model for execution
Two Models in your Suit Case, Planning and Building

Save plan in docs/plans/my-plan.md

---

Add Notifications Once Task Execution is Completed.
For Claude Code : cc-notify

---

Two honest caveats. First, cheaper models need clearer instructions — they follow a good plan well but improvise badly, so the weaker the model, the more the plan has to spell out. Second, don't over-optimize: switching models every few minutes costs you attention to save pennies. Default to a strong model, drop to a cheap one for the obvious chores, and leave it there.

## Rule of thumb: a strong model to decide what to do, a cheap model to do it. When a cheap model starts going in circles, that is your signal the task needed the stronger one — switch up, don't keep retrying.

Context is not one thing
Context is Layers:

Some Layers are Fixed, not under your control
Some Layers are Flexible, under your control, managable and is to be manages to control context rot.

## Figure out to reduce the Flexible Layers.

Context Window is the limit
20-30 messages and a few file lookups.

The tricky part: there is no warning that tells you "this conversation is getting too long." It just keeps growing quietly in the background.

AI gets worse at remembering things as the conversation grows.
Longer conversations cost more money.

once a session is past roughly half its window, that's your cue to /compact or /clear (next), not when it hits 100%.

Persistence Options:

1.  Saved in Session
2.  Saved in a plan.md file

The plan file acts as a backup in case you cannot resume the old conversation.

Tip: If you saved a plan file earlier (like docs/plans/my-plan.md), you can also start a fresh conversation and tell it: "Read docs/plans/my-plan.md and continue from step 4."

What if the AI made a mistake? You can undo it.

Do not panic — both tools let you roll back, in slightly different ways:
Claude -> Esc 2x or /rewind

Claude Code: Press Esc twice (when the input box is empty), or type /rewind. You get a menu of every prompt from the session; pick one and choose what to restore — the code, the conversation, or both. Note that this undoes the AI's own file edits, not things it did by running shell commands (a deleted or moved file won't come back this way). There's no "redo" — rewind jumps you to a chosen point rather than stepping back and forth, so rewind deliberately.

OpenCode: Type /undo to reverse the AI's last change, and /redo if you change your mind. This works by using git under the hood, so your project needs to be a git repository.

Either way, treat this as a safety net for experiments, not a substitute for git. For anything you want to keep, commit it — checkpoints and undo are session-level conveniences, not permanent history.

checkpoints and undo are session-level conveniences, not permanent history.

One small difference

Claude Code's undo covers file edits but not terminal commands. For example, if AI ran a command that deleted a file, undo will not bring it back.

OpenCode's undo covers everything (file edits and terminal commands) because it uses git to track all changes.

Coverage of Undo:
Claude Code: File Edits only
Open Code: File Edits + Terminal Commands
because it uses git to track all changes.

---

# Model Selection Commands

---

# Context Management Commands

Three Context Management Commands

1. /clear and /new [When the task changes]
2. /compact [Same task, less baggage]
3. /undo [Bad turn; revert]

How to know when the context goes bad ?
