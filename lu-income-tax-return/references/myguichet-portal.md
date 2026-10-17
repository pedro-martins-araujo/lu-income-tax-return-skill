# Working in the MyGuichet Modèle 100 form

How the online form behaves, learned by filling it end to end. The URLs and layout below are from the 2025 form (`fpgun-acd-f100-2025`); the year in the path changes every year. Pages, fields and wording can change from one year to the next: re-check the page order the first time you open a new year's form. Trust the form's own info boxes for that year's ceilings over any figure in these references.

## Contents
1. Access and saving
2. Navigation and page order
3. Interaction quirks (read before the first click)
4. Reading a page back
5. Section-by-section notes
6. What the person does at the end

---

## 1. Access and saving

- **Login.** The person logs in to MyGuichet.lu themselves (LuxTrust, eID). Never handle credentials.
- **Drafts.** The draft lives under "Mes démarches" → "ACD (Modèle 100) : Déclaration pour l'impôt sur le revenu de l'année YYYY" → **"Reprendre la démarche"**. Its reference looks like `YYYY-A123-B456`. Beware of stray duplicate drafts for the same year.
- **Save semantics:**
  - **"Suivant"** moves on but keeps the data only in the **server session**.
  - **"Sauvegarder"** writes the draft. **"Reprendre plus tard"** writes the draft and leaves the form.
  - The session expires after a period of inactivity. You see a "502 Bad Gateway" page, or the space page with `messageKO=message.error.technical`. **Unsaved pages are lost, including pages you already left with "Suivant".**
  - So click "Sauvegarder" after every page that changed. After a batch of changes, use "Reprendre plus tard", reopen with "Reprendre la démarche", and read the changed pages back to prove they persisted.
- **Recovering an expired session.** Open the procedure page (`…/fpgun-iep-front/space/procedures/<id>`) and click "Reprendre la démarche". The person stays logged in to MyGuichet even when the form session has expired.

## 2. Navigation and page order

- **Side menu.** Clicking an earlier section jumps back to it; later sections then show greyed out until you walk forward again with "Suivant". The data is kept.
- **Direct URLs.** Pages can be opened directly while a form session is active: `https://www.services-publics.lu/fpgun-acd-f100-YYYY/jsp/<page>.action`. Without an active session they bounce to the space page.
- **Bottom bar:** Précédent · Sauvegarder · Reprendre plus tard · Suivant · **Finaliser**. Never click "Finaliser"; it is the person's step.

Page order (2025), with the page names that appear in the URLs:

| Section | Pages (`.action` names) |
|---|---|
| Introduction | `edit_introduction_description` (consent box) |
| Eligibility | eligibility questions |
| Indications générales | informations générales · `edit_general_ratepayer` · `edit_general_ratepayer_address` · `edit_general_conjoint` · `edit_general_conjoint_address` · `edit_general_childrens` · signatures · pré-remplissage |
| Revenus | `edit_revenue_revenue` (income categories: these ticks decide which pages exist) |
| Salaries | `edit_salary_details` · `edit_salary_con_details` · `edit_salary_fo` · `edit_salary_con_fo` · `edit_salary_recap` |
| Capital income | `edit_movableCapital_exempt_income` (+ `_con`) · `edit_movableCapital_taxable_income` (+ `_con`) · `edit_movableCapital_recap` |
| Homes / rental | `edit_rentalIncome_net_income_interest` (one page per home) · `edit_rentalIncome_summary_rent_income` |
| Special expenses | `edit_specialExpenses_elements` (menu) · `_premium_insurance` · `_home_contributions` · `_social_contributions` · `_summary` |
| Extraordinary charges | `edit_charges_elements` (menu) · `edit_charges_domestic_charges` |
| Divers | `edit_various_dac6` |
| Recap | `edit_summary_taxable_income` |

## 3. Interaction quirks (read before the first click)

These caused most of the lost time:

1. **Every field triggers a server re-render when it loses focus.** Click the field, type, click an empty margin of the page, then wait 5–10 s. Text typed while a re-render is pending is silently dropped.
2. **Take a screenshot (or a small zoom) between fields.** When filling several fields in one batch, the next entry was dropped unless a screenshot was taken after the previous field's re-render. Background tabs do not render until captured. Verify every value afterwards anyway.
3. **The first click after a page load is often lost.** Check with a screenshot that it took effect, for example that a radio button actually changed.
4. **Custom dropdowns.** Click to open, then click the option. Type-ahead picks the first prefix match, which can be wrong when options share a prefix ("Financement habitation…" vs "Financement travaux"). Long lists (house numbers) need scrolling inside the list.
5. **Replacing a value.** Triple-click, then Ctrl+A, then type. For dates, type `dd/mm/yyyy` and click outside. A date picker may pop up; clicking outside closes it.
6. **"Ajouter …" buttons** (add a debt, a premium, an address) sometimes need a second click, and they shift the layout. Take a new screenshot before the next click.
7. **Radio buttons that change the page layout** (home status, Oui/Non questions) re-render large parts of the page. Values already typed in the remaining fields are usually kept.
8. **Coordinates go stale** after any re-render, window resize or scroll. Re-take a screenshot rather than reuse old coordinates.

## 4. Reading a page back

Use read-only JavaScript to list a page's values and compare them with the workbook. It does not change anything:

```js
location.pathname.split('/').pop() + ' ## ' +
Array.from(document.querySelectorAll('section input[type=text], section select, section textarea, section input[type=radio]:checked'))
  .map(e => {
    if (e.type === 'radio') { const l = document.querySelector('label[for="' + e.id + '"]'); return 'R:' + (l ? l.innerText : ''); }
    if (e.tagName === 'SELECT') return 'S:' + (e.options[e.selectedIndex] ? e.options[e.selectedIndex].text : '');
    if (/^\d{11,13}\s*$/.test(e.value)) return 'ID(present)';   // don't echo national ID numbers
    return e.value;
  }).join(' | ')
```

Joining with ` | ` matters: tool output containing `=` or `;` may be blocked as cookie-like data. Masking the 11–13-digit values keeps identity numbers out of the transcript.

## 5. Section-by-section notes

- **Indications générales**
  - **Address.** The current address is the address today (the time of filing). "Autres adresses au cours de l'année" must cover the **whole year**; otherwise the error "Veuillez renseigner obligatoirement toute l'année" appears. For a move, enter one line per address with its start and end dates.
  - **Address entry.** The postal code fills the locality and street; the house number comes from a dropdown.
  - **Spouse.** Same rules for the spouse ("même adresse" = Oui copies the current address only).
  - **Signatures.** Each spouse signs in their own name.
- **Revenus, categories page.** Ticking or unticking a category adds or removes whole pages. To remove interest that should not be declared, untick "Autres revenus de capitaux non visés ci-dessus" for each person. Keep the 50 %-exempt dividend line ticked.
- **Salaries**
  - One block per employer and period. Remuneration rows by nature; use "Autre (à spécifier)" for items such as "SI".
  - Exemptions sit in a separate "Déclaration d'exemptions" block.
  - The deductible contributions figure is computed by the form and must match line 11 of the certificate.
- **Capital income**
  - **Dividends.** Country, company name, company type ("Autre (à spécifier)" for forms not listed, e.g. S.à r.l.-S), gross amount, withholding.
  - **Recap.** It applies the flat-rate costs and the exempt slice; costs are spread pro rata across the columns.
- **Homes** (one page per home)
  - **Status:** "Librement disponible pendant toute l'année" / "… une partie de l'année" / "Indisponible/inachevé" / "Cédé gratuitement".
  - **Part-year.** This adds "Disponible depuis / jusqu'au", and per loan a required "Date de début du prêt" (the default is 01/01 of the year; replace it with the real date). It also gives two interest pairs, before and during availability.
  - **Each loan:** creditor, nature (Financement habitation/construction, Crédit relais, …), balance at 31/12, "100 % used to acquire this property?", optional financing costs, interest per spouse.
  - **Totals.** The form computes the ceiling per spouse. For the available part of a home in its first year it splits the household total 50/50 and may round up by a cent.
- **Special expenses**
  - The menu radios decide which pages appear.
  - Insurance: one entry per contract, with company, risk type and premium per spouse.
  - Home savings: pre-filled from last year; enter the contributions paid.
  - Social contributions: automatic.
  - The recap shows the ceilings.
- **Charges extraordinaires.** Childcare entries are pre-filled from last year: check the type ("Frais de garde d'enfant"), the person claiming, the period and the amount.
- **Divers.** The DAC6 questions are almost always "Non".
- **Recap.** It shows the net income per category, the special expenses and the **revenu imposable**. Reconcile this with the workbook.

## 6. What the person does at the end

1. Reopen the draft and click **"Finaliser"**. The form runs its own validation and lists the pages to fix.
2. Upload the attachments.
3. Check the IBAN for refunds, the identity numbers and the e-mail addresses.
4. Each spouse signs with their own means.
5. Click **"Transmettre"**.
6. Download the PDF of the filed return and keep it with the year's documents. It is next year's template.
