# keepingnewportsafe.com

A data-driven analysis of the NBFD Station 3 relocation, provided by the Newport Beach Firefighters Association.

Static single-page site. No build step. Deploys as-is to Netlify, GitHub Pages, or any static host.

## Contents

- `index.html` - the site
- `privacy.html` - privacy policy (linked from the comment form and SMS consent)
- `thanks.html` - post-submission confirmation page (form `action` target)
- `assets/nbfa-logo.png` - NBFA logo (blue)
- `assets/nbfa-logo-white.png` - NBFA logo (white, used in the footer)
- `assets/NBFA_Station3_Response_Capabilities_Analysis.pdf` - full report (download link)
- `assets/travel_time_comparison.png` - Figure 1, first-due travel time by area
- `assets/savings_charts.png` - Figure 2, confirmed working fire assembly curves
- `assets/station-hero.jpg` - hero background image (see PRE-PUBLISH CHECKLIST item 0)

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

## PRE-PUBLISH CHECKLIST

### Cleared as of August 3, 2026

- **TCPA / SMS review.** Counsel has reviewed the cell-phone opt-in consent language
  (recurring messages, autodialer disclosure, consent not a condition, message frequency,
  data rates, STOP and HELP) and the linked privacy policy, and the Association's
  messaging platform honors STOP and HELP.
- **FPPC disclosure review.** Counsel / the committee treasurer has confirmed the
  "Paid for by Newport Beach Firefighters Association PAC / Not Authorized by a candidate
  or a committee controlled by a candidate" attribution as it appears in the site footer.
  Note that as of the August 3 revision this disclosure appears on the **website only**.
  The executive summary PDF is published by the Association as an informational document
  and does not carry it.
- **NBFA leadership sign-off** on the executive summary PDF and the NBFA Facts section.
- **Hero image.** `assets/station-hero.jpg` is a Street View capture of the station, used
  at low visibility behind a 3px blur and a navy gradient overlay (86 to 95 percent
  opacity). The Association has reviewed and approved this use. Swapping in an NBFA-owned
  photograph is a drop-in replacement at the same path if one becomes available.

### Still open

1. **Reference [6] resolution number.** Add the July 28, 2026 resolution number and minutes
   link to reference [6] in `index.html` and to the References section of the PDF once
   posted. The PDF currently reads "Resolution number and minutes to be appended upon
   posting."
2. **Harbor Hills Views / Spyglass current-condition figure rests on an estimate.** The
   area is mapped at 33.60556, -117.85678. Its current first-due unit is Station 5, whose
   leg is a geometric **estimate** of 2.37 miles using a hillside routing factor (apparatus
   climb via Marguerite Ave and San Joaquin Hills Rd), not a measured route. The published
   current-condition figure of 4:41 depends on it. Replace with a measured driving distance
   from Station 5 (410 Marigold Ave) when available. The proposed-condition figure of 2:52
   is not affected.
3. **CAD validation, recommended before wide promotion.** Figures already include Opticom
   preemption on the eight Jamboree intersections identified by Public Works, cited in
   reference [13] as ECMS document 3157227. The portal requires a session, so the document
   was not machine-verified; confirm the intersection list against the record.
4. **Teamsters quotation, optional.** Insert the exact quotation and speaker from the
   July 2, 2025 Daily Pilot article, or keep the current "publicly reported" phrasing,
   which is accurate as written.
5. **Opportunity, not a blocker.** Consider pursuing preemption on the San Joaquin Hills,
   MacArthur, and Ford corridors. Those routes carry the Port Streets and Bonita Canyon
   responses and currently receive no preemption credit in this model, so improvements
   there would be additional to the results shown.

## Editing figures

Every travel time on this site derives from the response model workbook,
`NBFD_Station3_Response_Time_Model.xlsx` (not published on the site; held by the
Association). Travel time in seconds is `(0.65 + 1.7 x D x (1 - 0.2 x jamboree_share)) x 60`,
where `D` is the route distance in miles; the preemption reduction applies to the distance
term only, not to the 0.65-minute intercept. First-due is the minimum across all stations,
not Station 3 alone.

Three places must move together if the model changes: the `hoods` array in `index.html`
(which drives both the interactive map and the results table), the two figures in
`assets/`, and the executive summary PDF. Station and area coordinates are
Association-verified; the proposed Station 3 pin is the selected parcel coordinate
33.61518, -117.86764. One Ford Road has been removed; The Bluffs covers that area.
