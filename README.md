# Agency Tax Stack OS

B2B workflow software for online marketing agencies that are becoming software, AI, data, and creator-payment businesses.

The product classifies operational activity against tax-sensitive categories and produces **CPA-ready workpapers**. It does not prepare tax returns, file information returns, or give legal opinions.

## What this MVP does

- Import projects, expenses, vendors, payments, time, and payroll via CSV
- Classify projects for **§41 R&D candidates** vs ordinary advertising / market research
- Allocate development costs to **§174A domestic R&E** vs **§174 foreign R&E**
- Flag creator/contractor payments for **1099-NEC candidates**, **1099-K overlap**, missing W-9/TIN, and foreign payees
- Flag campaign spend for **§162 vs §274** review (meals, gifts, entertainment)
- Build a review queue with approve / exclude / request-info (audit logged)
- Attach evidence memos to projects and vendors
- Export CPA packets as JSON schedules

The demo workspace is **Northstar Growth Labs LLC**, a $1–5M agency with an attribution engine, offshore dashboard work, creator campaigns, and a proposed SaaS spinout.

## Run locally

You need Node.js 20+.

```bash
npm install
npx prisma db push
npm run db:seed
npm run dev
```

Open [http://localhost:4327](http://localhost:4327).

```bash
npm test        # classification + CSV validation tests
npm run lint
```

SQLite is used for the local demo (`prisma/dev.db`). Production should use PostgreSQL; swap the Prisma datasource URL when you are ready.

## Product boundaries

The UI labels items as **candidates for CPA review**, not as deductions, filings, or qualifications:

| The app says | The app does not say |
| --- | --- |
| Candidate for CPA review | Definitely deductible |
| §41 exclusion flag detected | Not allowed as a matter of law |
| 1099-NEC candidate | You must file Form 1099-NEC |
| QSBS readiness risk | QSBS-qualified |

## Stack

Next.js 15, React, TypeScript, Tailwind, shadcn/ui, Prisma, SQLite, Zod, Vitest.
