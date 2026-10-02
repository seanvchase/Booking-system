# InkBook

A reusable tattoo-artist booking platform inspired by the workflow of modern tattoo booking tools, built to be configurable for many artists rather than hard-coded to one brand.

## V1 included
- Public artist booking URL: `/book/[slug]`
- Tattoo-specific intake form
- Multi-artist database model
- Artist request inbox
- Status-ready workflow: new → needs info / consultation → approved → deposit pending → booked → completed / declined
- SMS notification hook through Twilio
- Appointment and notification-log tables
- Ayanna Luna / @inkbaby713 seed artist
- Mobile-first styling

## Setup
1. Create a Supabase project and run `supabase/schema.sql` in the SQL editor.
2. Copy `.env.example` to `.env.local` and fill in Supabase values.
3. For SMS, add Twilio credentials and an SMS-capable Twilio number.
4. Run `npm install` then `npm run dev`.
5. Open `/book/inkbaby713` for Ayanna's form and `/admin` for the current inbox.

## Before public launch
Add Supabase Auth/RLS to protect `/admin`; configure Storage for reference-image uploads; add artist onboarding/settings UI; add approval actions and secure client booking links; connect Stripe deposits; add availability/calendar rules; add email/push notifications; add consent/waiver flows; deploy to Vercel and attach a custom domain.

## Multi-artist design
Branding and behavior live in each `artists` row (`brand` and `settings` JSON), while requests and appointments reference `artist_id`. This lets the same deployment support many independent artists with unique slugs, notifications and settings.
