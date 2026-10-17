# Luxembourg income tax return skill (Modèle 100 on MyGuichet)

A skill for Claude that helps a Luxembourg resident, alone or as a jointly taxed couple, prepare and fill in the personal income tax return (*Modèle 100*, "déclaration pour l'impôt sur le revenu") on [MyGuichet.lu](https://www.myguichet.lu).

Claude:
1. asks for access to the folder with **this year's documents** and **last year's filed return**;
2. reads, renames and inventories the documents;
3. learns the household, the contracts and the form's layout from last year's return;
4. asks the questions the documents don't answer;
5. builds a **summary workbook**: every figure with its source, a comparison with last year, and the open items;
6. asks the person to **log in to MyGuichet**, then fills the draft page by page, reads every page back and saves;
7. reconciles the form's recap with the workbook and explains every difference with last year;
8. prepares a numbered **upload folder** and a hand-off checklist.

The person always logs in, signs and transmits themselves. The skill never types passwords, identity numbers or bank details.

> **Disclaimer.** This is not tax advice. The rules in `references/tax-rules.md` were written for tax year 2025 and change every year. Check them against official sources, and have an accountant confirm judgement calls with money at stake.

## Contents

```
lu-income-tax-return/
├── SKILL.md                         workflow and ground rules
├── references/
│   ├── tax-rules.md                 rules met in practice, with sources (verify yearly)
│   ├── myguichet-portal.md          page order, URLs, interaction quirks, saving
│   ├── document-checklist.md        documents per category and where they come from
│   └── questions.md                 interview questions
├── scripts/
│   └── build_summary.py             JSON → Excel summary workbook (needs openpyxl)
└── assets/
    └── example_return.json          fictional example of the JSON format
```

## Install

- **Claude Code (personal):** copy the `lu-income-tax-return` folder to `~/.claude/skills/`.
- **Claude Code (one project):** copy it to `<project>/.claude/skills/`.
- **Claude apps:** zip the `lu-income-tax-return` folder (or use a packaged `.skill` file) and add it under Settings → Capabilities → Skills.

Filling the form needs a browser Claude can drive, such as Claude in Chrome or the desktop app's built-in browser. The workbook script needs Python 3 with `openpyxl`.

## Use

Ask something like:
- "Let's do our Luxembourg tax return for 2025. Documents are in `~/Taxes/2025`, last year's return is in `~/Taxes/2024`."
- "I scanned my certificat de salaire and the bank interest certificates, can you check what goes where in the Modèle 100?"

## Privacy

- The skill works on documents in the person's own folders. **This repository contains no personal data:** every example is fictional.
- Keep returns, certificates and generated workbooks out of the repository; the `.gitignore` blocks common document types.

## Maintenance

Every year, before the filing season:
- update `references/tax-rules.md`: amounts, ceilings, new rules;
- update the form URL year in `references/myguichet-portal.md`;
- re-check the page order the first time the form is used.

Contributions with sources are welcome.

## Licence

MIT, see `LICENSE`. The rules summarised in `references/tax-rules.md` come from public Luxembourg sources, which are cited there.
