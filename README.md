# compound-interest
# Net Worth Forecast — Simple & Real‑world (Responsive, Vanilla JS)

A single‑file, framework‑free visual tool to plan how wealth grows while you’re working and how it depletes in retirement. Built with **HTML + CSS + SVG + vanilla JavaScript** — no build step, no dependencies.

## Why

Financial planning shouldn’t require a spreadsheet degree. This tool shows, at a glance, what happens to your net worth each year under steady assumptions ("Simple") and under more realistic, wobbly markets ("Real‑world").

## Features

* **Two modes**

  * **Simple Forecast:** one inflation and ROI.
  * **Real‑world Forecast:** set **min/max** for inflation and ROI; each year is drawn **deterministically** within those ranges so charts don’t flicker. Add **Black Swan** years (Recession, War, Pandemic, or Custom) to bump inflation (pp), cut ROI (pp), and raise expenses (%) for that whole year.
* **Stacked bar chart (one bar per year):**

  * **Carry‑forward** from previous year
  * **Contributions** (includes optional **windfall**)
  * **Interest** earned this year
  * **Withdrawals** this year
* **Gapless bars** for easier reading and continuous hover.
* **Live tooltips** (hover/touch): year, age, carry‑forward, contribution (with windfall note), interest, withdrawals, **withdrawals in today’s ₹**, and end‑of‑year balance.
* **Reference markers:** end of contributions, retirement, life expectancy.
* **Controls** (left sidebar on desktop, collapsible drawer on mobile):

  * Current year & age, current net worth
  * Monthly contribution, *contribute until age*, **contribution timing** (start/end of month)
  * Inflation & ROI (**or** ranges in Real‑world mode)
  * Retirement age, monthly income after retirement, **index income annually by inflation** (toggle)
  * **Windfall:** toggle, year & amount
  * **Stop at zero** (don’t allow negative balance)
* **Black Swan highlighting:** affected year’s bar is subtly **darkened**.
* **Responsive layout:** desktop (sidebar + 70% chart) and mobile (collapsible controls, big touch targets).
* **India‑friendly units:** inputs use **lakh units** – typing `1` means **₹1,00,000**. Actual rupee amounts are shown under fields.
* **Self‑tests** in the console validate core math (contributions, withdrawals, windfall, range equivalence).

## How it works (math)

* **Monthly compounding** for both ROI and inflation (annual → monthly via `(1+r)^1/12−1`).
* **Contributions** can be applied at the **start** or **end** of each month.
* **Withdrawals** (retirement income) start at the selected **retirement age** and can **step up once per calendar year** by inflation if indexing is enabled.
* **Present value of withdrawals** is computed by discounting each month’s withdrawal by the **cumulative monthly inflation factor** within the year and summarized per year for the tooltip.
* **Windfall** (if enabled) is applied **at the start of its calendar year**.
* **Real‑world mode:** per‑year inflation/ROI are drawn from the provided ranges using a **deterministic LCG**, so re‑renders are stable; Black Swan years modify that year’s parameters.

## Defaults (on load)

* Current age **35**; contribute until **45**
* Current net worth **₹50L**; monthly contribution **₹1L**
* Retire at **52**; monthly income **₹1.2L** (indexed annually by default)
* Inflation **7%**; expected ROI **11.5%**
* **Windfall:** off

## Getting started

1. Clone or download.
2. Open `index.html` (or the exported HTML file) in any modern browser. That’s it.

> No build step, no NPM. Everything runs client‑side.

## File structure

Single HTML file containing markup, styles, and script. The SVG chart uses a responsive `viewBox` so it scales cleanly on mobile and desktop.

## Known limitations

* Taxes, fees, asset allocation, and sequence‑of‑returns risk are **not** modeled.
* Inflation/ROI ranges are independent and not correlated across years.
* Black Swan effects are constant within the selected year and don’t bleed into adjacent years.
* All amounts are **pre‑tax**.

## Roadmap ideas

* Export chart as PNG/SVG and data as CSV.
* Scenario presets and bookmarking of parameter sets.
* Multiple portfolios / side‑by‑side comparisons.
* Optional tax & fee modeling.
* Keyboard shortcuts and improved accessibility.

## Contributing

Issues and PRs are welcome. Keep the project **framework‑free** and **single‑file** unless a change demonstrably improves simplicity or clarity.

## License

MIT