# Benny Cakeland — website + backend starter

This project includes:
- `index.html`: public bakery website; product catalogue reads from Supabase and order enquiries are saved to the database.
- `admin.html`: private admin sign-in, product management and order management.
- `supabase_setup.sql`: database tables, row-level security policies and sample products.

## 1. Create your Supabase project
1. Create a project at https://supabase.com/.
2. In Project Settings → API, copy the **Project URL** and **anon/public key**.
3. Open both `index.html` and `admin.html`.
4. Replace `YOUR_SUPABASE_PROJECT_URL` and `YOUR_SUPABASE_ANON_PUBLIC_KEY` in each file with your project values.
   - The anon/public key is intended for browser use when Row Level Security is correctly enabled.
   - Never put a `service_role` key in either HTML file.

## 2. Create the database
1. In Supabase, open SQL Editor → New query.
2. Paste all of `supabase_setup.sql` and run it.
3. This creates products, orders and user_roles tables, plus row-level security policies.

## 3. Create your admin login
1. In Supabase, open Authentication → Users → Add user.
2. Create your own admin email and a strong password. Do not share your password in chat.
3. Copy the new user's UUID from the Users page.
4. In SQL Editor, run this statement with the real UUID:
   `insert into public.user_roles (user_id, role) values ('YOUR-REAL-USER-UUID', 'admin');`
5. Admin access is now granted to that account only.

## 4. Run and publish
- For a quick local test, open `index.html` in a browser. Some browser setups may restrict scripts on local files; if so, run a simple local web server or deploy to a static host.
- Publish `index.html` and `admin.html` to the same hosting site (for example, Netlify, Vercel or GitHub Pages).
- Public website: your hosting domain.
- Admin dashboard: add `/admin.html` to your domain.

## 5. How it works
- Visitors can read active products and submit order enquiries.
- Submitted enquiries are stored in `orders` with `pending` status.
- Admins can sign in, view orders, update their status, and add/edit/delete products.
- The WhatsApp contact link uses Benny Cakeland's supplied number: +233 542 354 860.

## Important before going live
- Add your actual product names, prices, photos, delivery/pickup details and business hours.
- Test a customer order and test the admin dashboard before advertising the website.
- Configure Supabase Auth URL settings with your deployed site URL.
- Consider adding spam protection/rate limiting before public launch.
- This starter does not process card or mobile-money payments. Payment integration can be added separately.
