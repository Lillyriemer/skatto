Skatto — Full Implementation Instructions for Ronny

Visual source of truth: Homepage design based on 1920 px wide canvas (see attached image)

⸻

1. Product vision (non-negotiable)

Skatto is a single-purpose calculation tool.

It exists to answer one core question:

“Hur mycket bör jag lägga undan för skatt?”

Skatto is:
	•	calm
	•	friendly
	•	deterministic
	•	transparent
	•	non-scary

Skatto is not:
	•	a form
	•	a content site
	•	a dashboard
	•	an account-based service

Inputs describe reality.
Outputs describe consequences.

⸻

2. Global layout logic (applies to all pages)

All pages follow the same structure:
	1.	Minimal header (orientation + one action)
	2.	Calm hero framing (homepage only)
	3.	One dominant calculator card
	4.	Optional explanation below
	5.	Quiet footer with legal closure

Do not introduce additional navigation patterns.

⸻

3. Header (persistent)

Structure
	•	Left: Skatto logo (medium)
	•	Right: one button labeled “Beräkna”

Behavior
	•	Header is sticky
	•	Clicking logo scrolls to top
	•	Clicking “Beräkna” scrolls smoothly to the calculator card
	•	No navigation menu
	•	No dropdowns
	•	No login
	•	No language switch

Header must never trigger calculations.

⸻

4. Hero section (homepage only)

Purpose
	•	Build trust
	•	Reduce fear
	•	Set expectations

Content
	•	Large Skatto logo
	•	Tagline: “Skatt, utan krångel.”
	•	Three reassurance points:
	•	Inga konton. Inga krav. Bara en uppskattning.
	•	Snabbt – ofta under 1 minut.
	•	Perfekt för planering.

Rules
	•	No CTA buttons
	•	No interaction
	•	This section is informational only

⸻

5. Calculator section (core product)

Structure
	•	One large card with rounded corners
	•	Card uses gradient background
	•	Card contains tabs
	•	Only one tab visible at a time

Tabs
	1.	Enskildfirma
	2.	Anställning
	3.	Kryptoskatt

Tabs:
	•	Share the same layout
	•	Share the same visual hierarchy
	•	Represent different “modes” of the same tool

⸻

6. Tab logic

6.1 Enskildfirma tab

Purpose:
Calculate how much tax to set aside.

Inputs:
	•	Tax year (dropdown)
	•	Birth year (dropdown)
	•	Municipality (autocomplete input)
	•	Income excl. VAT
	•	VAT on income
	•	Costs excl. VAT
	•	VAT on costs
	•	Preliminary tax:
	•	Dropdown: months (1–12)
	•	Input: amount per month

Rules:
	•	All calculations update automatically
	•	No submit action
	•	Empty fields = 0
	•	Never show errors for missing input

Outputs (read-only):
	•	Yearly tax to set aside
	•	Monthly equivalent
	•	Derived yearly income

Outputs must never be editable.

⸻

6.2 Anställning tab

Purpose:
Calculate salary after tax.

Rules:
	•	Same layout as Enskildfirma
	•	Different inputs
	•	Calculates net salary
	•	Shows monthly and yearly results
	•	Automatic updates
	•	No submit button

⸻

6.3 Kryptoskatt tab

Purpose:
Calculate tax on crypto trades.

Phase 1 (now):
	•	File upload of trading history
	•	Automatic calculation

Phase 2 (later):
	•	Manual input option (not implemented now)

Rules:
	•	Upload is the primary path
	•	Manual entry must not be implemented yet

⸻

7. Input component rules

Tax year
	•	Dropdown only
	•	Valid tax years only
	•	No free text

Birth year
	•	Dropdown only
	•	Numeric years
	•	Used internally for tax rules
	•	Not displayed directly in results

Municipality
	•	Text input with autocomplete
	•	Typing “Fa” shows:
	•	Farsta
	•	Falun
	•	Falkenberg
	•	Selecting a municipality:
	•	Inserts full name
	•	Maps internally to correct kommunalskatt
	•	Users must not enter kommunalskatt manually

Preliminary tax
	•	Two linked inputs:
	•	Months (1–12)
	•	Amount per month
	•	Total = months × amount
	•	Missing values = 0

⸻

8. Results & calculation behavior
	•	Results are outputs only
	•	Results update automatically
	•	Never show:
	•	NaN
	•	undefined
	•	empty strings
	•	Incomplete input → display 0 kr

⸻

9. “Så räknar vi” (calculation explanation)

Default state

Shows only the first part of the calculation:
	•	Överskott
	•	Vinst
	•	Schablonavdrag
	•	Överskott (result)

Expanded state
	•	Clicking “Visa hela beräkningen” expands inline
	•	Reveals:
	•	Beskattningsbar inkomst
	•	Slutlig skatt
	•	Moms
	•	Betald preliminärskatt
	•	Total skatt / skattefordran
	•	No navigation
	•	No modal
	•	Same calculation, more detail

⸻

10. Typography

Font delivery

Primary font: Proxima Nova via Adobe Fonts

The following must be included in <head> on all pages:
<link rel="stylesheet" href="https://use.typekit.net/obx1wor.css">

Typography rules
	•	Sizes based on 1920 px wide canvas
	•	Sizes are desktop reference values
	•	Must scale responsively
	•	Hierarchy must remain intact
	•	Do not introduce new styles or weights

⸻

11. Colors

Background
	•	#F8F9FD

White
	•	#FFFFFF
Used for:
	•	form fields
	•	text on colored backgrounds

Gradient (cards & tabs)
	•	#7E8EC6 → #6389C6
	•	Vertical direction

Brand accents
	•	Logo smiley: #6A78B9
	•	Colored text on light background: #6389C6

Do not introduce additional colors.

⸻

12. Graphic assets (use as-is)

All assets are provided via GitHub links and must not be modified.
	•	Hook illustration (hero reassurance)
	•	Large logo (hero)
	•	Medium logo (header)
	•	Logo icon (lavender / off-white)
	•	Chaos illustration (footer)

Rules:
	•	No recoloring
	•	No animation
	•	Maintain aspect ratio
	•	Use only in intended context

⸻

13. Footer & legal structure

Footer must include links to:
	•	Om Skatto
	•	Kontakt
	•	Integritetspolicy
	•	Villkor
	•	Cookies

Footer also includes disclaimer text:

Skatto är ett beräkningsverktyg som ger uppskattningar baserat på gällande schabloner. Resultaten ersätter inte rådgivning från Skatteverket eller redovisningskonsult.

Footer structure must not be removed.

⸻

14. UX tone & error handling
	•	Never shame the user
	•	Never warn for missing input
	•	Missing input = 0
	•	UI must feel forgiving and calm

⸻

15. Guiding principle (do not violate)

Calm clarity over cleverness.
Trust over features.
One question, one answer.

⸻

Skatto — Full Implementation Instructions for Ronny

Visual source of truth: Homepage design based on 1920 px wide canvas (see attached image)

⸻

1. Product vision (non-negotiable)

Skatto is a single-purpose calculation tool.

It exists to answer one core question:

“Hur mycket bör jag lägga undan för skatt?”

Skatto is:
	•	calm
	•	friendly
	•	deterministic
	•	transparent
	•	non-scary

Skatto is not:
	•	a form
	•	a content site
	•	a dashboard
	•	an account-based service

Inputs describe reality.
Outputs describe consequences.

⸻

2. Global layout logic (applies to all pages)

All pages follow the same structure:
	1.	Minimal header (orientation + one action)
	2.	Calm hero framing (homepage only)
	3.	One dominant calculator card
	4.	Optional explanation below
	5.	Quiet footer with legal closure

Do not introduce additional navigation patterns.

⸻

3. Header (persistent)

Structure
	•	Left: Skatto logo (medium)
	•	Right: one button labeled “Beräkna”

Behavior
	•	Header is sticky
	•	Clicking logo scrolls to top
	•	Clicking “Beräkna” scrolls smoothly to the calculator card
	•	No navigation menu
	•	No dropdowns
	•	No login
	•	No language switch

Header must never trigger calculations.

⸻

4. Hero section (homepage only)

Purpose
	•	Build trust
	•	Reduce fear
	•	Set expectations

Content
	•	Large Skatto logo
	•	Tagline: “Skatt, utan krångel.”
	•	Three reassurance points:
	•	Inga konton. Inga krav. Bara en uppskattning.
	•	Snabbt – ofta under 1 minut.
	•	Perfekt för planering.

Rules
	•	No CTA buttons
	•	No interaction
	•	This section is informational only

⸻

5. Calculator section (core product)

Structure
	•	One large card with rounded corners
	•	Card uses gradient background
	•	Card contains tabs
	•	Only one tab visible at a time

Tabs
	1.	Enskildfirma
	2.	Anställning
	3.	Kryptoskatt

Tabs:
	•	Share the same layout
	•	Share the same visual hierarchy
	•	Represent different “modes” of the same tool

⸻

6. Tab logic

6.1 Enskildfirma tab

Purpose:
Calculate how much tax to set aside.

Inputs:
	•	Tax year (dropdown)
	•	Birth year (dropdown)
	•	Municipality (autocomplete input)
	•	Income excl. VAT
	•	VAT on income
	•	Costs excl. VAT
	•	VAT on costs
	•	Preliminary tax:
	•	Dropdown: months (1–12)
	•	Input: amount per month

Rules:
	•	All calculations update automatically
	•	No submit action
	•	Empty fields = 0
	•	Never show errors for missing input

Outputs (read-only):
	•	Yearly tax to set aside
	•	Monthly equivalent
	•	Derived yearly income

Outputs must never be editable.

⸻

6.2 Anställning tab

Purpose:
Calculate salary after tax.

Rules:
	•	Same layout as Enskildfirma
	•	Different inputs
	•	Calculates net salary
	•	Shows monthly and yearly results
	•	Automatic updates
	•	No submit button

⸻

6.3 Kryptoskatt tab

Purpose:
Calculate tax on crypto trades.

Phase 1 (now):
	•	File upload of trading history
	•	Automatic calculation

Phase 2 (later):
	•	Manual input option (not implemented now)

Rules:
	•	Upload is the primary path
	•	Manual entry must not be implemented yet

⸻

7. Input component rules

Tax year
	•	Dropdown only
	•	Valid tax years only
	•	No free text

Birth year
	•	Dropdown only
	•	Numeric years
	•	Used internally for tax rules
	•	Not displayed directly in results

Municipality
	•	Text input with autocomplete
	•	Typing “Fa” shows:
	•	Farsta
	•	Falun
	•	Falkenberg
	•	Selecting a municipality:
	•	Inserts full name
	•	Maps internally to correct kommunalskatt
	•	Users must not enter kommunalskatt manually

Preliminary tax
	•	Two linked inputs:
	•	Months (1–12)
	•	Amount per month
	•	Total = months × amount
	•	Missing values = 0

⸻

8. Results & calculation behavior
	•	Results are outputs only
	•	Results update automatically
	•	Never show:
	•	NaN
	•	undefined
	•	empty strings
	•	Incomplete input → display 0 kr

⸻

9. “Så räknar vi” (calculation explanation)

Default state

Shows only the first part of the calculation:
	•	Överskott
	•	Vinst
	•	Schablonavdrag
	•	Överskott (result)

Expanded state
	•	Clicking “Visa hela beräkningen” expands inline
	•	Reveals:
	•	Beskattningsbar inkomst
	•	Slutlig skatt
	•	Moms
	•	Betald preliminärskatt
	•	Total skatt / skattefordran
	•	No navigation
	•	No modal
	•	Same calculation, more detail

⸻

10. Typography

Font delivery

Primary font: Proxima Nova via Adobe Fonts

The following must be included in <head> on all pages:
<link rel="stylesheet" href="https://use.typekit.net/obx1wor.css">

Typography rules
	•	Sizes based on 1920 px wide canvas
	•	Sizes are desktop reference values
	•	Must scale responsively
	•	Hierarchy must remain intact
	•	Do not introduce new styles or weights

⸻

11. Colors

Background
	•	#F8F9FD

White
	•	#FFFFFF
Used for:
	•	form fields
	•	text on colored backgrounds

Gradient (cards & tabs)
	•	#7E8EC6 → #6389C6
	•	Vertical direction

Brand accents
	•	Logo smiley: #6A78B9
	•	Colored text on light background: #6389C6

Do not introduce additional colors.

⸻

12. Graphic assets (use as-is)

All assets are provided via GitHub links and must not be modified.
	•	Hook illustration (hero reassurance)
	•	Large logo (hero)
	•	Medium logo (header)
	•	Logo icon (lavender / off-white)
	•	Chaos illustration (footer)

Rules:
	•	No recoloring
	•	No animation
	•	Maintain aspect ratio
	•	Use only in intended context

⸻

13. Footer & legal structure

Footer must include links to:
	•	Om Skatto
	•	Kontakt
	•	Integritetspolicy
	•	Villkor
	•	Cookies

Footer also includes disclaimer text:

Skatto är ett beräkningsverktyg som ger uppskattningar baserat på gällande schabloner. Resultaten ersätter inte rådgivning från Skatteverket eller redovisningskonsult.

Footer structure must not be removed.

⸻

14. UX tone & error handling
	•	Never shame the user
	•	Never warn for missing input
	•	Missing input = 0
	•	UI must feel forgiving and calm

⸻

15. Guiding principle (do not violate)

Calm clarity over cleverness.
Trust over features.
One question, one answer.

⸻

End of instructions

This document is the single source of truth for Skatto’s implementation.

End of instructions

This document is the single source of truth for Skatto’s implementation.
