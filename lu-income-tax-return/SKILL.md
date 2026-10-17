---
name: lu-income-tax-return
description: Prepare, fill in and double-check a Luxembourg personal income tax return (Modèle 100, "déclaration pour l'impôt sur le revenu", sometimes called 100F) on MyGuichet.lu, for a single person or a jointly taxed couple. Use this whenever someone living in Luxembourg wants to do, prepare, review or file their tax return, gathers documents for it (certificat de salaire, certificats d'intérêts, épargne-logement / Bausparen, assurances, frais de garde, dividendes de leur société, achat ou vente de logement), asks what they can deduct in Luxembourg, or wants their return compared with last year's — even if they only say "help me with my taxes" or "let's do the déclaration". Not for company returns (Modèle 500, form 900 withholding declarations) or non-residents without Luxembourg income.
---

# Luxembourg personal income tax return (Modèle 100) on MyGuichet

You help a resident taxpayer (alone or with a spouse/partner taxed jointly) go from a folder of scanned documents to a complete, saved draft return on MyGuichet.lu. The person keeps control of everything that commits them: logging in, signing, transmitting.

What the person should have at the end:
1. A **saved draft** on MyGuichet with every page filled and re-read.
2. A **summary workbook** (Excel) listing every figure entered, its source document, the figure the form shows, a comparison with last year, and the open questions.
3. A folder **"To upload with the return"** with numbered copies of the supporting documents.
4. A short **hand-off checklist** for finalising, signing and transmitting.

A full return usually takes several sessions spread over days, so keep the person informed with one-line status notes and record decisions as you go (in the workbook's open items and, if memory is available, in memory).

## Ground rules, and why they matter

- **You are not a tax adviser.** Keep two things apart: *facts* (amounts copied from documents, which you can verify) and *treatment* (which line, which rule, which year). In real use the dangerous mistakes were not typos. They were the right number under the wrong rule, for example exempt home-savings interest declared as taxable income. Flag every treatment decision you make. When money is at stake, suggest the person's accountant confirms it.
- **Check the rule at source when it matters.** Tax rules change every year. `references/tax-rules.md` is a starting point, not an authority: before relying on a rule for a decision, confirm it on guichet.public.lu, impotsdirects.public.lu or Legilux, and cite the source. When the person questions an item, re-check the source instead of defending your first answer.
- **Never log in, sign, finalise or transmit.** The person logs in with LuxTrust or their eID, and only they click "Finaliser", sign and "Transmettre". You work inside their logged-in session.
- **Don't type identity or bank data.** Leave national identification numbers (matricules), IBANs and passwords exactly as pre-filled, and ask the person to check them on the signature step.
- **Save explicitly and often.** On MyGuichet, "Suivant" keeps data only in the server session, which expires. "Sauvegarder" or "Reprendre plus tard" is what writes the draft. See `references/myguichet-portal.md`.
- **Keep personal data where it lives.** Work in the person's folders. Don't copy documents or figures anywhere else (gists, public repos, shared links) without being asked.
- **Don't silently change last year's practice.** If last year's return did something you think is wrong, or something you would do differently, say so and let the person decide. They may have had an audit or an adviser's instruction you don't know about.

## Workflow

### Phase 0: Check what changed for this tax year

Tax law, ceilings, credits and the online form change every year, and the references in this skill describe one specific year (see the header of `references/tax-rules.md`). Before relying on them for a different year:

1. **Confirm the tax year** being declared. It is usually the previous calendar year: in 2027 people file for 2026.
2. **Look for this year's changes** on official sources. Search guichet.public.lu and impotsdirects.public.lu for "nouveautés fiscales <year>" or "ce qui change", and read the year's paper form and its explanatory notice. The form is at `https://impotsdirects.public.lu/dam-assets/fr/formulaires/pers_physiques/<year>/100f-<year>.pdf`, or found via the ACD forms page. Watch for new or changed ceilings, tax credits, exemptions, tax classes and rules on homes or interest.
3. **Compare with `references/tax-rules.md`.** Treat anything that changed, or that you could not confirm, as unverified for this year. During the return, prefer the figures the MyGuichet form itself shows (its info boxes state the current ceilings) and cite the source you used.
4. **Tell the person** in a few lines what changed compared with last year, and how it affects them. This also explains part of the year-on-year comparison later.
5. **Update the references.** If the person maintains this skill, offer to update `references/tax-rules.md` and the form year in `references/myguichet-portal.md`, and to add a line to the change log at the end of `tax-rules.md`.

### Phase 1: Folders and access

Ask for, and get access to:
- the folder for **this year's documents** (suggest `<root>/<year>/`, and create it if needed);
- **last year's filed return**: the PDF from MyGuichet ("Mes démarches" → last year's return → download), plus last year's supporting documents if available;
- optionally, where documents arrive: mailbox, cloud drive, the accountant's e-mails. Ask before searching mailboxes or drives, and search narrowly (sender, subject, year).

If the session cannot see a folder, ask the person to add it, or use the tool for requesting directory access if one exists.

### Phase 2: Inventory, rename, read

Read every document, including ones the person "just scanned". Rename each one to a consistent pattern so the folder doubles as the evidence list:

`<Category> - <Issuer> - <Person or account> - <Year or period>.pdf`, for example `Salary - EmployerName - Spouse - 2025.pdf` or `Mortgage interest - Bank 1234-5000 - 27.08 to 31.12.2025.pdf`.

Build an inventory of what each document proves and which return line it feeds. Flag unreadable pages, missing pages ("page 1 of 2"), documents for the wrong year, and documents that contradict each other or what the person said. `references/document-checklist.md` lists what to expect per category and where people usually find it.

### Phase 3: Learn from last year's return

Last year's filed return is the best template you have:
- **Household:** persons, children, dates, which spouse is "contribuable" and which "conjoint".
- **Categories and amounts:** which income categories and deductions were declared, with per-person splits.
- **Contracts:** loans and homes (occupation dates), insurance and home-savings contracts, childcare entries and the *type* chosen for each.
- **The form's layout:** MyGuichet pre-fills many of these from last year, so you will meet them again.

Note anything that looks unusual (an exemption not claimed, a category choice) as a question for the person, not as a correction.

### Phase 4: Interview

Ask only what the documents don't answer, a few questions at a time, and record each answer with its date. `references/questions.md` has the full list. The questions that change the most are:
- **Moves.** When did they really move, and what date does the commune register show? The tax office sees the register; a residence certificate may be in their documents. If the two differ, explain the consequences and let them choose.
- **Homes and loans.** Property bought or sold, refinancing, bridge loans. Which loan financed which home decides which interest is capped.
- **Their own company.** Dividends: the year the distribution was decided, whether it was paid, and the withholding tax paid.
- **Other income.** Interest or other income abroad, rental income, pensions, side activities.
- **Household changes.** Marriage or partnership, separation, births, children leaving.

### Phase 5: Working summary workbook

Describe every figure in a JSON file and build the workbook with the bundled script:

```bash
python scripts/build_summary.py <data.json> "<year folder>/Tax return <year> - summary.xlsx"
```

`assets/example_return.json` shows the format, with fictional data. Rows can hold numbers or formulas that refer to other rows by key, and each row carries its source document and a note. The script writes these sheets:
- **Summary:** key totals per person, the total shown by the form, and the difference.
- **Previous year:** last year against this year, with the change and an explanation.
- **Detail:** every line with its source.
- **Open items:** priority, topic, what you found, what the person must do.
- **Attachments:** the files to upload.

Formulas only get their values after recalculation. Recalculate before sharing: open and save the workbook in Excel or LibreOffice, or use the xlsx skill's recalculation script if available. Update the JSON and rebuild whenever something changes. The workbook is your reconciliation reference against the form.

### Phase 6: Fill the form on MyGuichet

1. **Login.** Ask the person to open MyGuichet.lu in the browser you control and log in. With a Chrome extension that is their real browser; with a separate built-in browser they must log in there. Then open "Mes démarches", the year's "ACD (Modèle 100)" draft, and "Reprendre la démarche", or start a new one.
2. **Work page by page.** Fill each page from the workbook, then read it back (the snippet is in the portal reference), compare it with the workbook and click "Sauvegarder".
3. **Use the portal reference.** `references/myguichet-portal.md` has the page order and URLs, the per-section quirks, and the interaction lessons. The lessons matter most: custom dropdowns, a re-render after every field, the first click lost, the save semantics, and recovering from an expired session.
4. **Questions mid-form.** When a page asks something you can't answer from the documents or the interview, ask the person rather than guess.

### Phase 7: Verify

- **Read-back pass.** Re-read every page after the last change. A session timeout can silently undo work that was never saved, so check that persisted values survive "Reprendre plus tard" and a reopen.
- **Reconcile.** The form's recap must match the workbook to the cent. Explain any difference: the form rounds splits between spouses and applies ceilings itself.
- **Compare with last year.** Explain every large change in one line each: income moved from salary to dividends, a new home, a ceiling stepping down, and so on.
- **Re-read when challenged.** If the person questions an item, re-read the source document and the rule.

### Phase 8: Hand-off

1. **Upload folder.** Copy the supporting documents into `<year>/To upload with the return/`, numbered in section order (`01 - Salary - …`). These are copies; leave the originals untouched. Leave out documents not used in the return.
2. **Checklist.** Give the person a short checklist:
   1. reopen the draft and click "Finaliser";
   2. upload the files;
   3. check IBAN, identity numbers and e-mail addresses;
   4. each spouse signs;
   5. "Transmettre";
   6. download the PDF of the filed return into the year folder as next year's template.
3. **Open items.** List what is still open, and which judgement calls they made knowingly.

## Judgement calls to surface every time

These are the decisions where a reasonable reading can be wrong. Present each one with the money at stake and the alternatives, and suggest the accountant confirms the ones worth more than a few hundred euros:
- **Loans across two homes.** Attributing interest between two homes after a purchase, sale, refinancing or bridge loan. Interest follows what the borrowed money was used for, and the ceilings differ per home.
- **Occupation date.** The occupation or "availability" date of a home: purchase deed, completion of works, move, or the register date.
- **Dividend year.** Decision date or payment date, and whether the withholding tax was actually paid.
- **Exempt or not.** Whether an income is exempt or already taxed at source (RELIBI interest, home-savings interest) and so must *not* be declared.
- **Contradictions.** Any case where a document and the person's statement disagree.

## Ending each session

Close with a short status: what is filled and saved, taxable income according to the form, decisions taken, open items, and what the person needs to do next.
