# Naruto Shadow Portfolio Theme — PRD v2.0

**Status:** Built (v1.0 reference implementation shipped)
**Date:** June 30, 2026
**Supersedes:** v1.0 draft

## What changed from v1.0

The original brief was strong on vision but light on a few decisions a real build needs to make. V2 closes those gaps and reflects what was actually built:

- **Tech stack locked**: a single dependency-free HTML/CSS/JS file rather than a framework. Zero build step, drag-and-drop deploy to any static host, and the easiest possible fork for non-developers. A React/Next.js port is still a reasonable Phase 2 if the theme needs routing or a CMS later, but it isn't required to hit the brief's goals.
- **One signature mechanic, not five competing ones**: of the brief's many animation ideas, the build commits to a single memorable device — a "chakra meter" scroll-progress bar with a glowing orb that travels the width of the nav as the visitor reads. It's restrained everywhere else on purpose (see Anthropic's design guidance on spending boldness in one place).
- **Content is data, not markup**: all profile, skills, project, experience, and testimonial copy lives in one `CONFIG` object at the top of the script. Re-skinning the entire site for a new person is a content edit, not a redesign.
- **IP-safety pass**: no official artwork, logos, screenshots, or quoted dialogue from the source anime are used anywhere. All icons, the village-skyline silhouette, and the leaf emblem are original geometric SVGs drawn for this project. Terminology (rasengan, sharingan, chakra, Hokage, etc.) is used the way a fan project uses genre vocabulary — as flavor and naming convention — not as reproduced copyrighted material. If this theme is ever distributed publicly or commercially, swap in fully original naming to stay clear of trademark concerns; the current build keeps it personal-portfolio-safe.
- **Accessibility made concrete**: `prefers-reduced-motion` disables the particle field, cursor follower, and reveal animations outright (not just slows them); every interactive element has a visible focus ring; the contract form has real `<label>` elements; the mobile drawer manages `aria-expanded`.

## Build summary

A single static file (`naruto-shadow-portfolio.html`) implementing all eight sections from the original brief: hero, ninja profile, jutsu arsenal, mission log, career path, testimonials, summoning contract, and footer. Verified in a headless browser across desktop and mobile viewports, in both day and night themes, with the project modal and contact form interaction tested end-to-end.

| Brief section | Shipped as |
|---|---|
| Hero | Full-bleed dark hero, animated ember particles, SVG skyline silhouette, two CTAs |
| Navigation | Fixed nav + chakra scroll-meter; mobile slide-in drawer |
| About | "Bingo book" stat card + animated proficiency bars |
| Skills | Jutsu cards with animated circular proficiency rings, hover glow |
| Projects | Mission cards with rank chips, click-to-expand debrief modal |
| Experience | Genin → Hokage vertical rank timeline |
| Testimonials | Quote cards styled as "allied shinobi" |
| Contact | Front-end contract form with success state; social links as clan icons |
| Theme | Night (default) / "Daytime Konoha" toggle |

## Customization guide (for whoever forks this)

1. Open `naruto-shadow-portfolio.html` and find the `:root` CSS variables block — six color tokens control the entire palette, light and dark.
2. Find the `CONFIG` object near the top of the `<script>` tag — edit name, bio stats, skills, projects, experience, and testimonials there. The page re-renders those sections from this object automatically.
3. The contact form currently only shows a front-end success message. Wire the `summonForm` submit handler to a real endpoint (Formspree, Netlify Forms, or a serverless function) before going live.
4. Replace the placeholder `href="#"` links (social icons, project live/repo links) with real URLs.

## Out of scope (unchanged from v1.0)

Multi-page routing, authentication, a blog/CMS, full 3D village explorer, and commission/e-commerce booking remain out of scope for this phase.

## Next steps

- Swap placeholder copy for the real person's bio, projects, and history.
- Optional: port to Astro or Next.js if multi-page growth (blog, case studies) is anticipated.
- Optional: add a Lighthouse pass once real images/assets are added, to confirm the >90 performance target still holds with real content weight.
