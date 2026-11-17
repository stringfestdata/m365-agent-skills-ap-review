# Microsoft 365 agent skills: AP review demo

Fictional accounts payable data and a small, readable skill for the Stringfest Analytics article. No coding setup is needed.

1. Extract the reader download.
2. In Microsoft 365 Copilot, open Agent Builder and create an agent. Copy the name, description, and agent instructions from `prompts.txt`.
3. In Configure, find Skills and open the menu beside Add > Upload. Upload `ap-review.zip` intact. This inner ZIP contains `SKILL.md` at its root. Do not upload the whole reader download as a skill. Menu wording may vary; Microsoft's guide calls this Skills > Add.
4. Review the attached skill, then switch Configure to Preview (called Try it in Microsoft's guide). Copy the first test prompt and the table from `sample-invoices.md` into the test conversation.
5. Check the gross input total (8 rows, USD 13,000), then try the boundary and missing-input tests in `prompts.txt`.

The `ap-review` folder contains the editable source. If you change it, rezip the folder's contents so `SKILL.md` is at the ZIP root before uploading to Agent Builder. Retest each destination separately.

For Excel, the same plain-text procedure is designed to avoid worksheet-specific commands. Put the `ap-review` folder in the custom skills location opened through Excel's Manage plugins & skills settings, then refresh. Test discovery and results in your account; a successful Agent Builder test does not prove Excel installation or execution. This download does not install or synchronize anything automatically.

The primary queues follow the order in `SKILL.md`. They are fictional teaching rules, not a production payment policy. Possible duplicates stay in the gross input total for reconciliation. Review all results before adapting the method to real work.

The Agent Builder preview was tested on November 17, 2026 with the baseline, approval-change, and missing-date prompts. Excel is an adaptation path, not a separately verified installation in this exercise.

Microsoft documentation: https://learn.microsoft.com/en-us/plugins/agent-builder-add-skills
