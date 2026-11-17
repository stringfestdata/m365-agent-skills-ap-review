---
name: ap-review
description: Use when asked to review an accounts payable invoice list, triage AP exceptions, or prepare an AP review summary from supplied invoice data and an as-of date.
---

# Accounts payable review

Version 1.0. Teaching example with fictional rules, not an organization's payment policy.

## Inputs and scope

Use only the invoice table supplied for this request (pasted, attached, or explicitly identified in an accessible workbook). Ask for the table and an explicit as-of date if either is missing. Do not silently choose today's date or retrieve unrelated files.

Required columns: RowID, Vendor, InvoiceNumber, AmountUSD, DueDate, Approval. This exercise assumes one open, unpaid invoice record per row, positive amounts in USD, and dates in YYYY-MM-DD format. If the data includes payments, credits, other currencies, or a different grain, ask how to handle them before calculating a review.

If required columns are missing, RowID is blank or not unique, or any amount is missing, nonnumeric, or nonpositive, explain the specific issue and stop before reporting totals. A missing or invalid DueDate, Vendor, InvoiceNumber, or Approval can instead be flagged per row. Never invent a value.

## Procedure

1. Preserve every source row and its RowID. Count rows and independently sum AmountUSD before assigning review queues.
2. Identify possible duplicates using Vendor + InvoiceNumber + AmountUSD. For this comparison only, trim leading/trailing spaces and ignore letter case in Vendor and InvoiceNumber. Do not remove punctuation, fuzzy-match names, or change displayed source values. A duplicate group requires all three fields to be present and valid. Flag every row in a matching group. This is a possible duplicate, not proof of an overpayment.
3. Assign each row exactly one primary queue using this priority order:
   - Possible duplicate: belongs to a duplicate group.
   - Missing data: a required non-amount field is blank or invalid. Valid Approval values are Approved and Pending, ignoring case and surrounding spaces.
   - Needs approval: Approval is Pending.
   - Overdue, approved: Approval is Approved and DueDate is strictly earlier than the as-of date.
   - Current, approved: Approval is Approved and DueDate is on or after the as-of date. An invoice due on the as-of date is not overdue.
4. Keep additional flags in the reason even when a higher-priority queue applies. For example, a duplicate can also be overdue or pending approval. Do not count the row twice in queue totals.
5. Reconcile the sum of queue row counts and amounts to the untouched input. Retain both rows of a possible duplicate in the gross input total. Do not present that total as the amount to pay or deduct suspected duplicates without a confirmed correction.

## Output

Return the review in the conversation unless the user requests a file or worksheet and that output is supported by the host. Do not assume an active worksheet or change source records.

Include:
- The as-of date, source identification, input row count, and gross input amount.
- A summary table with Queue, Row count, Amount USD, and RowIDs. Show all five queues, including zero queues.
- A detail table with RowID, Primary queue, Reason, and Suggested next check. Mention relevant source values in each reason.
- A reconciliation showing input versus categorized row counts and amounts, with the differences.
- Three concise follow-up checks grounded in the supplied records. Do not invent owners, causes, approvals, or vendor communications.

This skill prepares a review only. It does not approve invoices, execute payments, post accounting entries, or contact vendors. If a requested action is outside this scope, explain what the review can support.
