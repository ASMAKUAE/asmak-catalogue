ASMAK Flipbook Catalogue: hosting guide for IT
==============================================

WHAT'S IN THIS ZIP
  index.html     The flipbook page (page-turn animation, mobile reader/zoom, clickable Contents)
  pages/         26 page images (p01.jpg ... p26.jpg)
  ASMAK-Flipbook-Catalogue.pdf   Same catalogue as a PDF with working Contents links
  _headers       Security headers (Cloudflare Pages reads this file automatically)
  robots.txt     Tells search engines not to index the site

It is a plain static site: no server code, no database, no build step.
It works on any static host (Cloudflare Pages, SharePoint-hosted site, internal web server, IIS, nginx).


RECOMMENDED: CLOUDFLARE PAGES + CLOUDFLARE ACCESS (free for up to 50 users)
-----------------------------------------------------------------------------
A) Host the site
  1. Sign in at https://dash.cloudflare.com (create a free account if needed).
  2. Go to Workers & Pages > Create > Pages > "Upload assets" (direct upload).
  3. Name the project (e.g. asmak-catalogue) and upload the CONTENTS of this ZIP
     (index.html must be at the top level, next to the pages/ folder).
  4. Deploy. You get an address like https://asmak-catalogue.pages.dev
  5. (Recommended) Custom domains > add e.g. catalogue.asmak.ae

B) Restrict it to ASMAK staff only
  1. Open Zero Trust (https://one.dash.cloudflare.com) and choose the Free plan.
  2. Settings > Authentication: keep "One-time PIN" (email code), or connect
     Microsoft Entra ID / Google Workspace for single sign-on.
  3. Access > Applications > Add an application > Self-hosted.
     - Application domain: catalogue.asmak.ae (and/or asmak-catalogue.pages.dev)
     - Policy: Action = Allow, Include = "Emails ending in" @asmak.ae
       (or a list of specific emails / a user group).
  4. Save. Visitors now see a Cloudflare login page; only allowed emails get in.
  5. Tip: in the Pages project settings, enable Access for preview deployments too,
     so *.asmak-catalogue.pages.dev preview links are also protected.

UPDATING THE CATALOGUE LATER
  Replace the files in pages/ (and index.html if sent a new one) and upload again
  as a new deployment. The address and the access rules stay the same.


ALTERNATIVE: COMPANY INTRANET / SHAREPOINT
  Copy the folder to any internal web server (or a document library that serves
  HTML), keeping index.html and pages/ together. Or share the PDF on OneDrive /
  SharePoint with "People in ASMAK" permissions.

NOTES
  - The header font loads from fonts.googleapis.com. If that is blocked, the page
    falls back to the system font; everything else works offline.
  - No cookies, tracking, analytics or external data calls are used.
  - Tested in Chrome on desktop and on a phone-sized screen.
