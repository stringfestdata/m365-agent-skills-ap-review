# Microsoft 365 agent skills: AP review demo

Fictional accounts payable data and a small, readable skill for the Stringfest Analytics article. No coding setup is needed.

1. Extract the reader download. Open `ap-invoices.xlsx` in Excel: the Invoices worksheet contains the Invoices table in A5:F13, with eight invoice records. The missing due date and repeated invoice number are intentional.
2. In Microsoft 365 Copilot, open Agents > New agent. Configure AP Review Coach using the name, description, and instructions in `prompts.txt`.
3. In Configure > Skills, open the menu beside Add > Upload. Upload the inner `ap-review.zip` intact and inspect the attached skill. Do not upload the whole reader download as a skill. Microsoft's guide calls this Skills > Add; labels can vary.
4. In Configure > Knowledge, select Add knowledge > Browse files (the paperclip; tooltip Upload from device). Upload `ap-invoices.xlsx` and wait until it finishes preparing. This adds a copy as agent knowledge, not a live connection to your local workbook. Agent users can access information from embedded files.
5. Switch Configure to Preview (Try it in Microsoft's guide). Send the first test prompt from `prompts.txt`; no pasted invoice table is needed.
6. Check the source workbook/table, the eight rows, and the USD 13,000 gross total. Run the what-if approval test in the same conversation. Select New chat for the missing-date test; the workbook remains available as agent knowledge.

The `ap-review` folder contains the editable source. If you change it, zip that folder's contents with `SKILL.md` at the ZIP root before uploading. Replace the uploaded workbook when using a new export. Neither upload synchronizes automatically with your local files.

For Excel, put the `ap-review` folder in the custom skills location opened through Manage plugins & skills, then refresh. The procedure avoids worksheet-specific commands, but test discovery and execution in your account. A successful Agent Builder test does not prove Excel installation or execution.

The primary queues follow the order in `SKILL.md`. These are fictional teaching rules, not a production payment policy. Possible duplicates stay in the gross input total for reconciliation. Review results before adapting the method to real work.

The uploaded-workbook baseline, approval-change scenario, and missing-date test were verified in Agent Builder Preview on November 17, 2026. Excel remains an adaptation path, not a separately verified installation.

Microsoft documentation: https://learn.microsoft.com/en-us/plugins/agent-builder-add-skills
Workbook upload: https://learn.microsoft.com/en-us/plugins/agent-builder-add-knowledge
