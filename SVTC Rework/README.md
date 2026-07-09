# Silent Victory Training Center — New Website

A 4-page static site (Home, About, Programs, Contact) styled after the UFC.com
look: black/gold-yellow palette, condensed bold "Oswald" display type, and a
squared corner-bracket frame motif used as a structural device throughout.

Each page is fully self-contained — CSS and JS are inlined directly in every
HTML file (no separate `css/` or `js/` folders), so you can upload just these
four files.

## Files
```
index.html            Home
about.html             About Shane Valko
services.html          Programs (Wrestling / Jiu-Jitsu / Strength / Chiropractic)
contact.html            Contact form + map + socials
manage-images.html      Upload-your-own-photo tool (see below)
```

## The "Manage site photos" page
`manage-images.html` (linked quietly from the footer of every page) lets you
pick a photo from your device for each image slot on the site and preview it
immediately — no code editing required.

**How it actually works, and its real limit:** there's no server behind this
site, so there's nowhere to permanently upload a file to. The page instead
saves your photo, resized, into your browser's local storage, and every page
checks that storage on load and swaps the image in if it finds one. That
means:
- ✅ Great for previewing a new photo instantly, in your own browser.
- ❌ It will **not** show up for other visitors to the live site — they're
  looking at their own browser, with no saved photo, so they still see the
  original.
- ❌ Clearing your browser data (or switching browsers/devices) resets it back
  to the original photos.

**To change a photo for everyone**, the image file itself needs to be
replaced on your web host — either upload a new file with the same name to
overwrite it, or update the `src` in the HTML to point at a new file, then
re-deploy.

Note: because the styling and script are duplicated in every file, if you
want to change something like a color or the nav, you'll need to make that
edit in all four HTML files. If this project grows, it's worth moving back
to a shared `style.css` / `main.js`.

## Things you'll want to do before this replaces silentvictorytc.com

1. **Swap the hotlinked images for your own files.** Right now the logo and a
   few photos are pulled directly from the current silentvictorytc.com so you
   can preview the design with real assets. Download `logo.png` and the slide
   images and host them locally (e.g. an `/img` folder) instead of linking to
   the old site.

2. **Real photos.** I can't pull photos from Instagram directly — there's no
   tool available to me that logs into or scrapes it, and Instagram blocks
   that kind of access without the account owner authorizing it (Graph API +
   business account). Every photo currently on the site is hotlinked from the
   gym's own existing site (`silentvictorytc.com/img/...`) rather than stock
   imagery, so it's real, but not new. To bring in fresh shots from Instagram:
   download them directly from the `@silentvictorytc` account (save-as from
   the app or a tool like Instaloader run by the account owner) and drop them
   into a local `/img` folder, replacing the `src` attributes.

3. **Connect a real Instagram feed.** I can't pull live photos from a private
   or business Instagram account — that needs the account owner's own
   authorization. The easiest path:
   - Use a no-code embed tool like **LightWidget** or **SnapWidget** — log in
     with the `@silentvictorytc` account, generate an embed snippet, and drop
     it into the "Latest From @silentvictorytc" section on `index.html` in
     place of the four placeholder tiles.
   - Or use Meta's official **Instagram Graph API** if you want full control
     (requires converting to/confirming an Instagram Business account and
     generating a long-lived access token).

4. **Wire up the contact form.** It currently just shows a confirmation
   message in the browser and doesn't send anywhere. Point it at a form
   backend like Formspree, Netlify Forms, or your own email service.

5. **Hosting.** These are plain static files — they'll work on any static
   host (Netlify, Vercel, GitHub Pages, or whatever currently serves
   silentvictorytc.com). Just upload the folder contents to replace what's
   there now.

## Design notes
- Fonts: **Oswald** (headlines) + **Barlow** (body), loaded from Google
  Fonts — a free pairing that mirrors UFC's squared, condensed, aggressive
  house type (UFC's actual "UFC Sans" is a proprietary custom font not
  available for outside use).
- Palette: black/near-black backgrounds, a gold-yellow accent, and a deeper
  amber tied to Shane's championship background (NCAA title, All-American
  honors).
- A squared corner-bracket frame is reused as a photo frame, a background
  device, and a section divider — the one signature element the design is
  built around.
