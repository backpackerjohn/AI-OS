# Desktop — Adding Customer — Unsold Page

*Structure and layout reference. Describes the sections, their arrangement, and the content each contains. Does not describe behavior or functionality.*

---

## Overall Layout

The page is a single desktop view composed of three stacked/adjacent regions:

1. A **top bar** running across the full width.
2. A **header block** below it, centered.
3. A **two-column body**: a wide **main content column** on the left and a narrower **sidebar** on the right.

The header block spans the full width above the two columns. The main content column and sidebar begin on the same line, directly beneath the header.

---

## Top Bar

A horizontal bar across the top of the page.

- **Left:** breadcrumb trail — Customers / Active / Customer Detail.
- **Right:** two action buttons — Edit and Save.

---

## Header Block

Centered, full-width, sitting above both columns.

- **Customer Name** — large, centered text.
- **Chip row** — a centered row of three chips directly beneath the name:
  - Status chip (e.g. *Unsold*)
  - Lead Source chip (e.g. *Walk-In*)
  - Contact chip (e.g. *Text*)
- **AI Summary** — a centered paragraph beneath the chip row; a short summary of the customer.

### Lead Source — Picker Behavior

Clicking the middle chip (the lead-source one, now with a caret) does the following:

- **Expands inline** — a panel opens in normal document flow directly below the chip row, pushing the AI summary and everything below it down, with a ~0.28s max-height/opacity animation. It's not an overlay.
- **Four equal-width cards in one row:** Walk-In, CRM, Referral, Social. Each has an uppercase muted title (not clickable) with all sub-sources listed beneath as clickable rows, all visible at once.
- **Leaf-only selection** — titles aren't clickable, so you can't land on a bare parent. Walk-In's single row is its own selectable leaf.
- **Immediate commit** — clicking a row updates the chip, no Apply step, and the panel collapses.
- **Chip label** reads `CRM · Dealer Wizard`, `Social · FB Marketplace`, etc., or just `Walk-In`.
- **Reopen highlights** the current selection with a dark fill so it's clear what's set.
- **Close** via clicking the chip again, clicking outside, or Escape. The caret flips and the chip darkens while open.

### Contact — Picker Behavior

Works just like the lead-source picker, except there are no sub-categories. Clicking the Contact chip (now with a caret) does the following:

- **Expands inline** — a panel opens in normal document flow directly below the chip row, pushing the AI summary and everything below it down, with the same ~0.28s animation. It's not an overlay.
- **Flat list of five options** in a single row of equal-width clickable rows: Text, CRM Text, Email, Snapchat, Facebook. No category titles, since there are no sub-sources.
- **Single select, immediate commit** — clicking an option updates the chip and collapses the panel, no Apply step.
- **Chip label** reads just the chosen value, e.g. `Email`.
- **Reopen highlights** the current selection with a dark fill.
- **Close** via clicking the chip again, clicking outside, or Escape. The caret flips and the chip darkens while open.
- **One picker at a time** — opening the Contact picker closes the Lead Source picker, and vice versa.

---

## Action Row

A centered row of two buttons sitting below the header block and above the main content column and sidebar.

- **Start Interview** — opens the interview overlay (see Interview Window).
- **Vehicle Selector** — function to be defined.

---

## Main Content Column (Left)

A two-column grid of cards. Some cards occupy a single column; two cards span the full width of the grid.

**Card order and width:**

- **Customer Info** — full width
- **Insurance** — half width
- **New Vehicle** — half width
- **Trade-in** — full width
- **Goals** — half width
- **Timeline & Notes** — half width

### Card: Customer Info
Fields: First Name, Middle Initial, Last Name, Date of Birth, Phone, Email, Street Address, City, State, Zip, Driver's License Number, DL State, DL Expiration. A *Lead Origin* sub-section (Source, Lead Generated Date, Additional Interests Note) sits at the bottom of the card.

### Card: Insurance
Fields: Insurance Company, Agent Name.

### Card: New Vehicle
Fields: Stock #, Year, Make, Model, VIN, Miles, Purchase Date.

### Card: Trade-in
A header with a *Has trade-in?* control — a **Yes/No chip pair, defaulting to Yes** — followed by trade vehicle fields: Year, Make, Model, Trim, Mileage, VIN, and Trade Valuation / Equity Estimate. A *Still owe on it?* control sits within the card — also a **Yes/No chip pair, defaulting to Yes** — followed by lien fields: Lienholder, Payoff Amount, Monthly Payment, Months Remaining. Choosing No on either chip pair hides its associated fields. These fields are linked with the interview's Trade section and the Customer Trade sidebar card — entering a value in any one of them fills the others.

### Card: Goals
A *Paying Cash* control, followed by: Monthly Payment Range (min / max), Money Down, Estimated Credit Score. Monthly Payment Range, Money Down, and Estimated Credit Score are linked with the interview's Payment section and the Payment Goals sidebar card — entering a value in any one of them fills the others.

### Card: Timeline & Notes
Three labeled sub-sections:
- **Relationship Cadence** — Last Contacted, Next Cadence Due, Referral Status.
- **Custom Follow-Ups** — a list of follow-up entries (date + reason).
- **Notes** — a note-entry field followed by a feed of notes, each tagged by origin (AI Discovery / Manual Entry) with a timestamp.

---

## Sidebar (Right) — Tools

A narrower column to the right of the main content, beginning on the same line as the Customer Info card. The sidebar itself has no visible border or container; it holds a vertical stack of rounded, filled tiles (bento-style).

It is titled **Tools** (header at the top with a collapse arrow) and is **collapsible**: clicking the collapse arrow slides the entire sidebar closed to the right side, and the main content widens to fill the space. When collapsed, a slim pull-out tab appears on the right edge to bring the sidebar back out.

**Tiles, top to bottom:**

- **Customer Wants** — two labeled sub-sections, **Vehicle** and **Features**. The card auto-fills from the interview: each time an option is selected in the interview's Vehicle or Features section, it appears here as a small chip in the matching sub-section; deselecting it in the interview removes the chip. An empty sub-section shows a muted dash. Because the card lives on the sidebar, it stays visible after the interview is closed. Only the interview's Vehicle and Features selections feed this card — the Trade form does not.
- **Customer Trade** — a compact card that auto-fills from the interview's Trade section as fields are entered; each filled field shows as a small label/value row, and an empty card shows a muted dash. The same values appear in the main Trade-in card.
- **Payment Goals** — a compact card that auto-fills from the interview's Payment section (Credit Score, Money Down, Payment Range) as fields are entered; same compact label/value rows, with an empty card showing a muted dash. The same values appear in the main Goals card.
- **Interview** — title-only placeholder
- Timeline
- Documents
- Notes

(Tiles other than the auto-filling cards above are titles only for now; content to be defined.)

---

## Interview Window

Opened by the **Start Interview** button in the Action Row below the header. It opens as an **overlay covering the main-content cards** (the header block and the Tools sidebar remain visible alongside it). It is titled **Interview** and is dismissed via a close (✕) button.

Below the title is a **navigation row of four equal-width boxes** — Vehicle, Features, Trade, Payment — bordered with rounded corners, the active one filled dark (Vehicle active by default). Clicking a box shows that section's content and hides the others; only one is active at a time, and selections persist when switching between them. The nav row stays fixed at the top while the section content below scrolls if needed.

All option choices throughout are **multi-select** — clicking toggles a dark fill on/off, and any number can be selected.

### Section: Vehicle

- **New / Used** — selectable option buttons (no heading).
- **Body** — Sedan, SUV, Truck, Van.

Selecting options here auto-fills the **Vehicle** sub-section of the Customer Wants card in the Tools sidebar (see Sidebar — Tools).

### Section: Features

Selectable options grouped under sub-headings:

- **Driver Assistance & Safety** — Adaptive Cruise Control, Blind Spot Monitor, Forward Collision Warning, Lane Departure Warning, Lane Keep Assist
- **Comfort & Convenience** — Heated Seats, Cooled Seats, Heated Steering Wheel, Power Driver Seat, Power Passenger Seat, Sunroof / Moonroof, Leather Seats
- **Technology** — Apple CarPlay, Android Auto
- **Performance & Drivetrain** — FWD, RWD, AWD
- **Interior & Seating** — 3rd Row Seating, 7 Passenger Seating, 8 Passenger Seating

Selecting options here auto-fills the **Features** sub-section of the Customer Wants card in the Tools sidebar (see Sidebar — Tools).

### Section: Trade

Mirrors the main Trade-in card: a *Has trade-in?* Yes/No chip pair (default Yes), then Year, Make, Model, Trim, Mileage, VIN, Trade Valuation / Equity Estimate; a *Still owe on it?* Yes/No chip pair (default Yes), then Lienholder, Payoff Amount, Monthly Payment, Months Remaining. Choosing No on either chip pair hides its associated fields. Values entered here sync to the main Trade-in card and the Customer Trade sidebar card. (The Trade section does not feed the Customer Wants card.)

### Section: Payment

Fields: Estimated Credit Score, Money Down, and Payment Range for New Car (From / To). Values entered here sync to the main Goals card (Estimated Credit Score, Money Down, Monthly Payment Range) and feed the Payment Goals sidebar card.
