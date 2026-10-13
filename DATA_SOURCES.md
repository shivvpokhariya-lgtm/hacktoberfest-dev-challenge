# WrenchWise — price data sources & methodology

The fair-price ranges in `PRICE_PACKS` (inside `index.html`) are **indicative baselines**,
not quotes. They exist so the app can flag *suspicious* line items conservatively —
a flag means "ask about this," not "this price is definitively wrong."

## How the ranges were built

Ranges were compiled in October 2026 from publicly published Indian service-price
sources, then widened slightly on both ends so the app under-flags rather than
over-flags. Where sources disagreed, the wider envelope won. Labour is bundled
into most ranges (that's how Indian garages quote); parts-only listings were used
only as a sanity floor.

Actual prices vary by city, car model/segment, and whether the garage is an
authorised service centre or independent. A hatchback in Indore and a luxury
sedan in Mumbai will not — and should not — land in the same band.

## Sources (all observed October 2026)

### India
- **MyCarHelpline — "Car Servicing Wear and Tear Items"**
  https://www.mycarhelpline.com/index.php?option=com_latestnews&view=detail&n_id=756&Itemid=10
  Indicative cost table (hatch-to-sedan): brake pads ₹2,000–3,500; brake discs
  ₹5,000–9,000; clutch (petrol) ₹4,000–10,000 / (diesel) ₹10,000–20,000; shock
  absorber pair ₹3,000–5,000; battery (petrol) ₹2,600–4,200 / (diesel)
  ₹4,000–7,000.
- **GoMechanic (official service pages, e.g. wheel care)**
  https://gomechanic.in/car-wheel-alignment-balancing-near-me
  First-party published prices, e.g. complete wheel care @ ₹1,349 with a
  GoMechanic vs authorised-centre vs local-mechanic comparison chart.
- **Bajaj General Insurance blog — wheel alignment & balancing costs**
  https://www.bajajgeneralinsurance.com/blog/motor-insurance-articles/difference-between-wheel-alignment-and-balancing.html
  Published India table: alignment ₹500–800 (2-wheeler) / ₹1,000–1,500
  (4-wheeler); balancing ₹150–300 per wheel.
- **Cartoq — clutch replacement costs**
  https://www.cartoq.com/car-clutch-replacement-signs-tips-cost/
  Clutch repair ₹6,000–12,000; up to ₹50,000 for expensive cars.
- **Moglix (GoMechanic brake-pad listings)** — parts-only price floor
  https://www.moglix.com/brands/gomechanic/automotive/spare-parts/brake-pads/125151400
  Per-model part prices (e.g. brake pad sets ₹569–₹1,100); installed prices add labour.

### United States (marked beta in the app)
- **YourMechanic — brake pad replacement guide**
  https://www.yourmechanic.com/services/brake-pads-replacement
  Standard brake pad replacement typically $200–$500 per axle; per-car estimate
  pages break out parts vs labour.
- **RepairPal** — per-repair price estimators (parts + labour by vehicle)
  https://repairpal.com/
  Widely quoted ranges, e.g. brake pads ~$335–$394. The US pack is deliberately
  small (14 jobs) and labelled beta until more estimator pages are cross-checked.

## What this document is not

- Not a price survey: no scraping, no API, no statistically sampled dataset.
- Not financial or purchasing advice: a GREEN flag doesn't mean "pay it," and a
  HIGH flag doesn't prove you're being cheated — it means the number deserves
  one sharp question.
- Ranges will drift as prices move. If a range looks stale, open an issue with a
  published source and it'll get updated.

## Contributing better data

The highest-leverage contribution to this project isn't code — it's a published
price list. If you run a garage or an aggregator with public rates, or you spot
a range that's off, PRs against `PRICE_PACKS` with a source link are welcome.
