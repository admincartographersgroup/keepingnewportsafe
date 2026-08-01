# keepingnewportsafe.com

A data-driven analysis of the NBFD Station 3 relocation, provided by the Newport Beach Firefighters Association.

Static single-page site. No build step. Deploys as-is to Netlify, GitHub Pages, or any static host.

## Contents

- `index.html` - the site
- `privacy.html` - privacy policy (linked from the comment form and SMS consent)
- `thanks.html` - post-submission confirmation page (form `action` target)
- `assets/nbfa-logo.png` - NBFA logo (blue)
- `assets/NBFA_Station3_Response_Capabilities_Analysis.pdf` - full report (download link)
- `assets/map_before_after.png`, `assets/map_delta.png`, `assets/units_on_scene.png` - static figures

## Comment form (Netlify)

The Support Public Safety section posts to a Netlify form named `council-comments`.
Netlify detects it automatically on deploy from the `data-netlify="true"` attribute
and the hidden `form-name` field; no build step or configuration is required.
Submissions appear under Forms in the Netlify dashboard and are stored there only.
Nothing is sent to any third-party service, CRM, or email provider.

Fields: `first_name`, `last_name`, `street_address`, `email` (all required),
`cell_phone` (optional), `sms_consent` (only shown when a 10-digit cell number is
entered), `comments` (required). `company` is a honeypot field for spam and is
hidden from users.

To receive notifications: Netlify dashboard, Forms, Form notifications, add an
email notification for `council-comments`.

## Deploy

Netlify: drag the folder into the Netlify dashboard, or connect the repo and set publish directory to the repo root. No build command.

GitHub Pages: Settings > Pages > deploy from branch, root directory.

The interactive map loads Leaflet and OpenStreetMap tiles from public CDNs; it requires a live internet connection and will render on any published host. OSM attribution is included and must remain.

## PRE-PUBLISH CHECKLIST (do not skip)

000. TCPA / SMS REVIEW. The cell-phone opt-in uses express written consent language
(recurring messages, autodialer disclosure, consent not a condition, message frequency,
data rates, STOP and HELP) and links to `privacy.html`. Have counsel confirm the wording
and the privacy policy before enabling any text program, and confirm the Association's
messaging platform honors STOP and HELP automatically.

00. DISCLOSURE REVIEW. The footer of the site and the PDF carry: "Paid for by Newport Beach Firefighters Association PAC / Not Authorized by a candidate or a committee controlled by a candidate." Before publishing, confirm with counsel or the committee treasurer: (a) whether California FPPC rules require the committee ID number alongside the committee name on this communication, (b) whether the PAC or the Association is the correct paying entity, since attribution elsewhere on the site reads "Newport Beach Firefighters Association," and (c) whether an issue-advocacy communication of this type triggers the disclosure requirement at all.

0. Hero image: `assets/station-hero.jpg` is a Street View capture of the station, used at low visibility behind a 3px blur and a navy gradient overlay (86 to 95 percent opacity). The Association has reviewed and approved this use. Swapping in an NBFA-owned photograph is a drop-in replacement at the same path if one becomes available.

1. Station and area coordinates are Association-verified (Apple Maps). Driving distances to all affected areas are Association-measured routes. Edit the `stations`, `sta3`, and `hoods` arrays in `index.html` if anything changes.
   NOTE: Harbor Hills Views / Spyglass is mapped at 33.60556, -117.85678. The Station 5 leg into that area is a geometric ESTIMATE of about 2.4 miles using a hillside routing factor (apparatus climb via Marguerite Ave and San Joaquin Hills Rd). Replace with a measured driving distance from Station 5 (410 Marigold Ave) when available; the current-condition figure of 4:41 depends on it.
   NOTE: One Ford Road has been removed; The Bluffs covers that area.
2. Add the July 28, 2026 resolution number and minutes link to reference [6] in `index.html` and to the References section of the PDF once posted.
3. Insert the exact Teamsters quotation and speaker from the July 2, 2025 Daily Pilot article, or keep the current "publicly reported" phrasing, which is accurate as written.
4. Confirm NBFA leadership sign-off on the report PDF and the NBFA Facts section.
5. Recommended before wide promotion: validate model figures against NBFD CAD data. Figures already include Opticom preemption on the eight Jamboree intersections identified by Public Works, cited in reference [13] as ECMS document 3157227. The portal requires a session, so the document was not machine-verified; confirm the intersection list against the record before wide promotion.
6. Consider pursuing preemption on the San Joaquin Hills, MacArthur, and Ford corridors. Those routes carry the Port Streets and Bonita Canyon responses and currently receive no preemption credit in this model, so improvements there would be additional to the results shown.

## Editing figures

The travel time figures in the map (`hoods` array), the results table, and the PDF derive from the network model documented in the report's Methodology section. If CAD-validated figures replace them, update all three places.
