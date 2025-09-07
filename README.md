# Crestmoor STS — Website

Modern, multi‑page **Next.js (App Router)** site with Tailwind and local UI primitives.
No external UI kit required. Deploy-ready on **Vercel** or **Netlify**.

## Quickstart

```bash
pnpm i   # or npm i / yarn
pnpm dev # http://localhost:3000
```

## Tech

- Next.js 14 (App Router) + React 18
- TailwindCSS (no custom plugins required)
- Local UI primitives (Button, Card, Badge, Input)
- lucide-react icons

## Structure

- `app/` — pages: `/` (landing), `/portfolio`, `/programs`, `/tech`, `/contact`, `/annex`
- `components/` — layout & blocks
- `components/ui/` — simple shadcn‑style primitives
- `public/` — add your images/renders here

## Classified Annex Gate

- Demo token generation happens client‑side in `/contact` and is verified naïvely in `/annex`.
- Replace with **Server Actions** or an API route that issues and verifies signed tokens, stores NDA receipts, and serves files from a protected storage bucket.

## Hooking Up Email/CRM

- Add a Server Action in `app/contact/actions.ts` to post the form to your CRM (HubSpot/Airtable) or send an email (Resend/SendGrid).
- For example, with Resend:
  - `pnpm i resend`
  - Create an action to call `new Resend(API_KEY).emails.send(...)`

## Deploy

- Push to GitHub, import on Vercel, set Node 18+.
- Environment vars (if you add email/CRM): `RESEND_API_KEY`, etc.

## Branding & Copy

Swap text and placeholders with STS doctrine, portfolio renders (Lightcraft Alpha, AEGIS, Armor Systems, FlameNet), and legal language for export control & compliance.

## Environment Variables

- `ANNEX_SECRET` — HMAC secret for signing/validating annex tokens
- `RESEND_API_KEY` — (optional) if you wire up email via Resend

## Wiring Email (Resend)

1. `pnpm i resend`
2. Uncomment the lines in `app/contact/actions.ts`
3. Set `RESEND_API_KEY` env
4. Call the server action from the contact form (already stubbed)
