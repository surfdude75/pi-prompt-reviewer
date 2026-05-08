# pi-prompt-reviewer

Clear prompts lead to better coding results, but typos, awkward wording, and
small misunderstandings can waste precious context, especially for people
writing in a second language. This extension puts a fast, lightweight reviewer
in front of your main pi session so weak prompts get cleaned up before they
create extra churn, making prompt review easy enough to become a habit and
helping you avoid the frustration of watching a long task fail because the
original request was unclear.

`pi-prompt-reviewer` is a [pi](https://pi.dev) extension that reviews your
prompt before it is sent to the main session.

## Features

- intercepts normal prompts before they are sent
- rewrites prompts for clarity while preserving intent
- can include recent conversation context when useful
- lets you choose the reviewer model and thinking level
- shows a confirmation dialog before the reviewed prompt is sent
- displays token usage and cost for the review step
- retries once with a safe fallback if the reviewer returns no text

## Install

### From GitHub

```bash
pi install git:github.com/surfdude75/pi-prompt-reviewer
```

### From a local checkout

```bash
pi install /path/to/pi-prompt-reviewer
```

After installing or editing the extension, reload pi:

```text
/reload
```

## How it works

1. Type a normal prompt.
2. Press Enter.
3. The extension reviews it with a lightweight model.
4. A dialog shows the review result.
5. Choose:
   - `Yes` to load the reviewed prompt
   - `No` to restore the original prompt
6. Press Enter again to send the prompt currently in the editor.

## Bypasses

These inputs are not reviewed:

- slash commands such as `/help`
- `!` shortcuts
- prompts with image attachments

To skip review once for a normal prompt, prefix it with a backslash:

```text
\send this directly without review
```

## Usage

### Enable or disable prompt review

```text
/prompt-review on
/prompt-review off
/prompt-review toggle
```

### Show status or help

```text
/prompt-review status
/prompt-review help
```

### Configure context mode

```text
/prompt-review context
/prompt-review context off
/prompt-review context smart
/prompt-review context always
```

Context modes:

- `off`: do not send recent conversation context
- `smart`: send the previous user prompt and last assistant reply only for
  referential follow-ups
- `always`: always send the previous user prompt and last assistant reply when
  they exist

### Configure reviewer model

```text
/prompt-review model
/prompt-review model auto
/prompt-review model <model-pattern>
```

Examples:

```text
/prompt-review model openai-codex/gpt-5.4-mini
/prompt-review model haiku
```

Notes:

- `auto` prefers a lightweight available model
- the default auto-selected model may not be supported by your subscription
- if review fails, choose another model with `/prompt-review model <model-pattern>`

### Configure reviewer thinking

```text
/prompt-review thinking
/prompt-review thinking off
/prompt-review thinking minimal
/prompt-review thinking low
/prompt-review thinking medium
/prompt-review thinking high
/prompt-review thinking xhigh
```

Recommended default:

- model: `auto`
- thinking: `off`

This is usually the best balance of speed, cost, and review quality.

## What the result dialog shows

The dialog can show:

- whether context was sent
- reviewer model
- thinking level
- token usage
- cost
- summary, notes, and clarification questions

## Retry behavior

If the first reviewer run returns no text, the extension retries once using the
current session model with thinking set to `off`.
