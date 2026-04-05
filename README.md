Vāyu Travels — Website
A clean, multilingual, single-file travel website for an India-based travel company. Built with vanilla HTML, CSS, and JavaScript — no frameworks, no dependencies, no build step.

Live Demo
Deploy the zip to Netlify (see below) and your site is live in under 60 seconds.

What's Inside
netlify-deploy/
├── index.html        # Entire site — all pages, styles, and logic
├── _redirects        # Netlify SPA routing rule
└── netlify.toml      # Security headers + cache config

Pages
PageDescriptionHomeHero slideshow, stats bar, featured destinations, testimonial carousel, CTADestinationsAll 9 destinations with category filters and detail modalsAbout UsCompany story, values grid, full team cards with hover biosServicesPackage tours, custom itineraries, corporate travel — tabbed layout

Languages
The language switcher (globe icon, top-right) supports 12 languages out of the box. Every visible string — navigation, headings, body copy, form labels, filter buttons — switches instantly with no page reload.
CodeLanguageenEnglishesEspañolfrFrançaisdeDeutschitItalianoptPortuguêsja日本語zh中文arالعربية (RTL layout auto-applied)hiहिन्दीko한국어ruРусский
To add a new language, add an entry to the LANGUAGES array and a matching key block in the T object inside index.html. Arabic is the only RTL language included; any new RTL language will automatically inherit the RTL layout because the dir attribute is set on <html> at runtime.

Destinations
Nine destinations are configured, each with category tagging, rating, best season, duration, price-from, and a full detail modal.
DestinationStateCategoryRajasthanRajasthanHeritageKeralaKeralaNatureHimalayasHimachal / SikkimAdventureGoaGoaBeachesVaranasiUttar PradeshCultureMumbaiMaharashtraCityHampiKarnatakaHeritageLadakhJammu & KashmirAdventureAndaman IslandsAndaman & NicobarBeaches
Adding a destination
Find the ALL_DESTINATIONS array in index.html and append a new object following this shape:
js{
  id: 'mysore',                          // unique slug
  name: 'Mysore',
  state: 'Karnataka',
  category: 'heritage',                  // heritage | nature | adventure | beaches | culture | city
  tag_key: 'filter_heritage',            // matches filter button key in T object
  rating: '4.7',
  duration: '3–5 days',
  best: 'Oct–Feb',
  img: 'https://…unsplash url…',
  color: '#8a5a3a',                      // badge background colour
  desc_en: 'English description here.',
  desc_es: 'Spanish description here.',  // add as many languages as needed
  highlights: [
    { icon: '🏯', label: 'Must See', val: 'Mysore Palace' },
    { icon: '📅', label: 'Best Time', val: 'Oct – Feb' },
    { icon: '🎆', label: 'Festival',  val: 'Dasara' },
    { icon: '💰', label: 'From',      val: '₹35,000' },
  ],
}

Team
Eight team members are configured in the TEAM array. Each card shows a portrait photo, name, role, social links, and a bio that appears on hover.
To add or edit a team member:
js{
  name: 'Sunita Rao',
  role_en: 'Head Guide, Kerala',         // add translations in TEAM_ROLES object
  img: 'https://…unsplash url…',         // use &fit=crop&crop=faces for best results
  bio_en: 'Short bio shown on hover.',
}

Design Tokens
All visual variables are defined as CSS custom properties at the top of index.html. Change them once and the entire site updates.
css:root {
  --sand:       #f5f0e8;   /* light section backgrounds */
  --ivory:      #fdfaf5;   /* page background */
  --clay:       #c4795a;   /* primary accent — buttons, tags, highlights */
  --spice:      #a0522d;   /* hover state for primary accent */
  --ink:        #1a1612;   /* headings and dark sections */
  --mist:       #8a8178;   /* body text, subtitles */
  --nav-h:      72px;      /* navbar height — adjusts all dependent spacing */
  --font-serif: 'Cormorant Garamond', Georgia, serif;
  --font-sans:  'DM Sans', sans-serif;
  --r:          6px;       /* global border radius */
}

Fonts
Loaded from Google Fonts via a single <link> tag. No font files are bundled.
FontUseCormorant GaramondAll headings, hero titles, brand nameDM SansBody copy, navigation, labelsNoto Sans JPAuto-applied when Japanese is activeNoto Sans SCAuto-applied when Chinese is activeNoto Sans ArabicAuto-applied when Arabic is activeNoto Sans DevanagariAuto-applied when Hindi is activeNoto Sans KRAuto-applied when Korean is active
To use self-hosted fonts for better performance, download the font files, place them in a fonts/ folder, and replace the Google Fonts <link> with @font-face declarations.

Deploy to Netlify
Option A — Drag and drop (fastest)

Go to app.netlify.com
Add new site → Deploy manually
Drag vayu-travels-netlify.zip onto the upload area
Done — you get a live *.netlify.app URL in ~10 seconds

Option B — GitHub (recommended for ongoing work)

Push the contents of netlify-deploy/ to a GitHub repository
In Netlify: Add new site → Import from Git
Select the repo — no build command needed, publish directory is .
Every git push to main triggers an automatic redeploy

Custom domain

Site settings → Domain management → Add custom domain
Point your registrar's DNS to Netlify's nameservers or add an A record to 75.2.60.5
Netlify auto-provisions a free SSL certificate via Let's Encrypt within minutes


Booking Form
The enquiry form inside the modal is currently front-end only — it collects data but does not submit anywhere. To wire it up:
Option 1 — Netlify Forms (zero config)
Add data-netlify="true" and name="enquiry" to the <div class="modal"> wrapper, wrap the fields in a <form> tag, and Netlify intercepts submissions automatically. View responses in the Netlify dashboard under Forms.
html<form name="enquiry" method="POST" data-netlify="true">
  <!-- existing fields -->
  <button type="submit">Send Enquiry</button>
</form>
Option 2 — External service
Connect the submit button to any service (Formspree, EmailJS, HubSpot, etc.) by posting the field values to their API endpoint in the button's onclick handler.

Performance Notes

Single HTTP request for the entire page (no JS bundles, no CSS files)
All images are lazy-loaded via loading="lazy"
Hero slideshow images are the only eagerly loaded assets
Google Fonts uses display=swap to prevent layout shift
Estimated Lighthouse performance score: 90–96 on a fast connection


Browser Support
Works in all modern browsers. Requires ES6 (arrow functions, template literals, const/let). Does not support IE11.

License
All source code in this repository is proprietary. Images are sourced from Unsplash under the Unsplash License — free for commercial use, no attribution required. Replace with your own photography before launch for brand authenticity.

# Built for Vāyu Travels · New Delhi, IndiaShare