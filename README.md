# draft-ar-followups

A Claude skill that turns an invoice into a ready-to-send payment follow-up email. No placeholders, no forms to fill in — upload an invoice, optionally add a line of context, and get an email you can paste into your mail client and send.

## What it does

- Reads the invoice (and any email thread or notes you include) and works out the collection stage from the due date: pre-due nudge, due-date check-in, early overdue, escalated, or mature (60+ days) — with tone that gets more pointed as the invoice ages, the way dunning should.
- Handles the states that override aging: payment already sent, disputes and PO mismatches, partial payments, and missed payment promises.
- Never outputs placeholders. If no contact name is on the invoice, it opens with "Dear Accounts Payable team," and signs with the sender identity found in your material.
- Stays safe to send: it won't claim an invoice is unpaid without evidence, won't invent late fees or legal threats, and won't reproduce unverified bank details.

## Example

Input: an invoice for $12,400 due May 5, no contact name, today is July 15.
Prompt: *"chase this invoice for me pls"*

```
Subject: Action required: INV-2214, 71 days past due

Dear Accounts Payable team,

Invoice INV-2214 for $12,400.00, due May 5, is now 71 days past due.
We need to resolve this promptly.

If payment has been released, please send the remittance details so we
can trace and apply it. If it remains unpaid, please reply by July 17
with a confirmed payment date and let us know of any issue that has
been holding it up.

Best regards,
Accounts Receivable
```

## Install

**Claude (Cowork / desktop):** download [`draft-ar-followups.skill`](draft-ar-followups.skill) and open it in Claude, then click **Save skill**.

**Claude Code:** copy this folder into `~/.claude/skills/draft-ar-followups/`.

## Usage

Attach an invoice (PDF, image, or text) and say things like:

- "chase this invoice"
- "this is due next week, send a quick nudge"
- "they're holding payment over a PO mismatch, draft a reply"
- "they promised payment last Friday and nothing arrived"

## Repo structure

```
SKILL.md                            # the skill definition
references/collection-playbook.md   # dunning stages, tone examples, decision order
evals/evals.json                    # test cases with assertions
examples/                           # sample invoices and a sample output
```

## Testing

The skill was benchmarked against its previous version on three scenarios (mature overdue, pre-due, PO dispute): 16/16 assertions passed vs. 10/16 for the old version, which failed consistently on placeholder sign-offs and report-style output.

## License

MIT
