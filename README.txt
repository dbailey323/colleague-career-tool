Holcim UK Talent Hub - colleague pages for Blink
Prepared 15th October 2026

WHAT THIS IS
Four static HTML pages, the colleague-facing part of the Talent Hub. No server-side code, no database, no sign-in logic. Host the folder as-is and open index.html.

FILES
  index.html                  Landing page, "Your career tools" (was For Colleagues)
  career-reflections.html     Career Reflections
  development-plan.html       Development Goals / IDP builder
  nextgen-behaviours.html     NextGen Growth Behaviours
  vendor/                     React 18.3.1, React DOM 18.3.1 and Babel standalone 7.29.0, bundled locally

Keep the four pages and the vendor folder together in one directory. Links between the pages are relative, so the folder can sit at any path.

WHAT WAS CHANGED FROM THE LIVE VERSIONS
  - Links between pages rewritten from Apps Script "?page=" form to plain relative links.
  - The Apps Script link-fixing snippet at the bottom of each page removed (it only ran on Google hostnames).
  - React, React DOM and Babel now load from vendor/ instead of unpkg.com, so no public CDN is needed.
  - A viewport meta tag added where it was missing (Apps Script used to inject it).
  - Nothing else. Content and behaviour are identical to the live Talent Hub.

HOSTING REQUIREMENTS
  - Serve over HTTPS. Career Reflections and the IDP tool save the colleague's own entries in browser localStorage and nothing is sent anywhere; this needs a stable origin, so the pages must stay on one domain and path.
  - Allow outbound access to fonts.googleapis.com and fonts.gstatic.com. The pages load Montserrat and Reddit Sans from Google Fonts. If that is blocked the pages still work but fall back to the system font. Tell Talent if you would rather the fonts were bundled locally too.
  - The pages compile their own JSX in the browser via Babel, so a Content Security Policy must allow inline scripts and 'unsafe-eval'. If Blink enforces a strict CSP, say so and the pages can be pre-compiled instead.
  - Career Reflections opens a new tab for "Download as PDF" (window.open then print). Pop-ups must not be blocked for the host domain.

OUTBOUND LINKS (open in a new tab, unchanged)
  SuccessFactors, CareerHub (holcim.gloat.com), Holcim UK Academy (aggregate.csod.com), Holcim University and NextGen pages on connect.holcim.com, Percipio.

Contact: Liv Adamowicz, Head of Talent.
