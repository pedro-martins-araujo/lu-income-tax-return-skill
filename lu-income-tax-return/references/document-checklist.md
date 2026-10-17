# Documents to collect, and where they usually come from

Use this as a checklist when building the inventory (Phase 2). Not every household needs every line.

| Category | Document | Typical source | Feeds |
|---|---|---|---|
| Last year | Filed return (PDF) | MyGuichet → Mes démarches → last year's return → download | Template, pre-fills, comparison |
| Salary | Certificat de salaire, de retenue d'impôt et de crédits d'impôt bonifiés, one per employer | Employer or payroll provider (Feb–Mar); for a director of their own company, the company's accountant | Salary pages |
| Pension | Pension certificate | CNAP / foreign pension fund | Pension pages |
| Own company | Shareholder resolution distributing a dividend; withholding declaration (form 900) and proof of payment; annual accounts only for context | Accountant | Capital income (50 % exempt) |
| Bank interest | Interest certificates for investment accounts abroad; RELIBI interest is not declared | Bank | Capital income |
| Home loans | **Interest certificate per loan account**, including loans closed during the year | Bank e-banking document area (e.g. "e-doc"), usually January | Homes page |
| Refinancing / purchase | Loan statements showing drawdowns and repayments; loan offers/contracts | Bank | Attributing loans to homes |
| Purchase / sale | Notary deed; notary's statement of costs (décompte), which separates loan costs from purchase costs | Notary (paper or e-mail), sometimes only on request | Homes page, financing costs |
| Residence | Commune certificate of change of residence; check its date | Commune / MyGuichet "Déclaration de changement de résidence" | Address history, occupation dates |
| Insurance | Fiscal certificates (deductible part) for life, death/outstanding-balance, accident, health, civil liability, vehicle | Insurers (Jan–Mar) | Special expenses |
| Home savings | Annual account statement per contract (payments, interest, payouts) | Bausparkasse | Special expenses (contributions only) |
| Old-age provision | Certificate (art. 111bis / PEPP) | Insurer / bank | Special expenses |
| Donations | Receipts from approved bodies | Charities | Special expenses |
| Childcare | Invoices or annual statements per child (crèche, maison relais, foyer scolaire, childminder), amounts actually paid | Commune / provider | Extraordinary charges |
| Domestic help / care | Invoices, payslips, CCSS statements | Provider / employer of the help | Extraordinary charges |
| Children | Births, custody, studies abroad | Person | Household page |
| Foreign income | Foreign statements and tax paid abroad | Foreign bodies | Relevant pages, tax credit |

**Naming convention:** `<Category> - <Issuer> - <Person or account> - <Year or period>.pdf`. For several documents of the same kind, add what tells them apart (account number tail, period, "page 1 of 2").

**Folder layout:**
```
<root>/
  <year-1>/                      last year's documents + filed return PDF
  <year>/                        this year's documents (renamed)
    To upload with the return/   numbered copies, created at the end
    Tax return <year> - summary.xlsx
```

**When a document is missing**, add it to the open items with where it is likely to be. Don't hold up the rest of the return for it.
