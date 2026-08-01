# InsightTech Solutions — Website

Static site (no backend required). Contact form sends email via EmailJS.

## 1. Set up EmailJS (free, no backend)

1. Sign up at https://www.emailjs.com and verify your email.
2. **Email Services** → Add Service → connect Gmail (or any provider) → copy the **Service ID**.
3. **Email Templates** → Create Template. Use these variables in the template body/subject:
   `{{from_name}}`, `{{from_email}}`, `{{phone}}`, `{{category}}`, `{{title}}`, `{{message}}`
   Copy the **Template ID**.
4. **Account** → **General** → copy your **Public Key**.
5. Open `index.html`, find this block near the bottom (inside the last `<script>` tag) and fill in your keys:
   ```js
   const EMAILJS_PUBLIC_KEY  = "YOUR_PUBLIC_KEY";
   const EMAILJS_SERVICE_ID  = "YOUR_SERVICE_ID";
   const EMAILJS_TEMPLATE_ID = "YOUR_TEMPLATE_ID";
   ```
6. Save, open the site, submit the form — you should receive an email. EmailJS free tier allows 200 emails/month.

Form validation (name, email format, 10-digit phone, category, title, description length) runs entirely in the browser before anything is sent — invalid fields are highlighted with an inline error message and nothing is submitted until they're fixed.

## 2. Deploy to Vercel

**Option A — Vercel dashboard (easiest)**
1. Push this folder to a GitHub repo (or drag-and-drop the folder at https://vercel.com/new).
2. In Vercel: **Add New → Project** → import the repo.
3. Framework preset: **Other** (it's a static site — no build step needed).
4. Root directory: leave as-is (project root).
5. Click **Deploy**.

**Option B — Vercel CLI**
```bash
npm i -g vercel
cd insighttech-website-main
vercel        # first deploy, follow prompts
vercel --prod # deploy to production
```

`vercel.json` is already included with clean URLs and sensible caching/security headers — no extra config needed.

## 3. Theme

The site now defaults to a **light theme** (was dark navy before). Core colors live in `:root` at the top of the `<style>` block in `index.html` if you want to adjust the palette further. The footer is kept as an intentional dark band for contrast — a common pattern on light sites — you can lighten it too by editing the `<footer style="background:#0B1220;">` line if you'd rather have a fully light page end to end.
