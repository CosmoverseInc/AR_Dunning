---
name: draft-ar-followups
description: Draft ready-to-send accounts-receivable payment follow-up emails from an invoice and optional context. Use whenever the user shares an invoice (file or details) and wants any payment communication — a reminder, nudge, chase, dunning email, pre-due note, overdue follow-up, promise-to-pay check-in, or dispute follow-up — even if they only say "chase this" or "write to them about payment."
---

# Draft AR Follow-ups

The user gives you an invoice and maybe a line of context. Return one polished, ready-to-send email — not a report, not a template to fill in. The goal is that the user can paste it into their mail client and hit send without editing anything.

## Workflow

1. Read the invoice and all supplied context (emails, notes, statements). Extract: customer name, contact name and email if present, invoice number, invoice date, due date, payment terms, amount, PO/reference, and any prior replies, promises, or disputes.
2. Get today's date from the system and compute days until or past the stated due date. When a due date is stated, use it rather than recomputing from terms; if the two conflict, mention it in a flag line after the draft.
3. Read `references/collection-playbook.md` and pick the stage. Account state overrides aging: payment received > payment in transit > active dispute > partial payment > missed promise > days overdue.
4. Draft the email using the playbook's tone and example for that stage, following the rules below.

## Rules that keep the email sendable and safe

- **No placeholders, ever.** Nothing like [Name], [Your Company], <date>, or XX. If the contact's name is unknown, open with "Hi team," or "Dear Accounts Payable team,". Sign off "Best regards," followed by the sender's name or company if it appears anywhere in the invoice or context, otherwise "Accounts Receivable". Every date and amount in the email must come from the supplied material — never invent one.
- **Don't assert what you can't see.** An uploaded invoice is not proof it's unpaid. Unless the user or a record confirms nonpayment, phrase the ask conditionally: request current status, and remittance details in case payment has already been sent. Say "our records show" only if records were actually supplied.
- **Label amounts correctly.** Refer to the invoice amount as the invoice amount; call it the "outstanding balance" only when a ledger, statement, or the user confirms nothing has been paid.
- **No invented consequences.** No late fees, service suspension, collections, credit reporting, or legal language unless supplied terms or policy support it. 60+ days past due justifies a pointed tone and a firm ask — not threats.
- **Never reproduce bank details** from an unverified or changed source.
- Match firmness to the stage and let it rise with age, as the playbook shows. Avoid stale filler: "friendly reminder," "gentle reminder," "kindly do the needful," "at your earliest convenience," "we understand things get busy."
- Keep the body to roughly 75–150 words; go longer only for multiple invoices or a dispute.

## Output

Return exactly this, and nothing more:

```
To: <only if a real recipient email or name is in the material — otherwise omit this line>
Subject: ...

<email body>
```

If one material fact is uncertain — the due date is ambiguous, amounts contradict each other — still draft the best possible email, then add at most two lines starting with "Note:" telling the user what to verify. Only decline to draft when the amount, customer, or due date is so unreadable or contradictory that any email would be wrong; in that case say in one or two sentences exactly what you need.

If an email tool is available, prepare a draft only. Never send without the user's explicit approval of the final recipients, subject, and body.
