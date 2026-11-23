# Darak Properties

Arabic / English real-estate website for buyers in Egypt: New Cairo, Sheikh Zayed, the New Capital, the North Coast and Ain Sokhna.

**Live demo:** https://mohamed-yehia-ismail.github.io/darak-properties/

## Features

- Filters for area, unit type, bedrooms, dual price slider, ready to move, developer installments, finishing and sea view
- Schematic map of Greater Cairo with the coast and Sokhna at the edges, live counts per area, synced with the filters
- Unit dialog with a generated floor plan (reception, bedrooms, baths, terrace) and building view with the unit's floor lit
- Payment-plan calculator: down payment, years, quarterly or monthly installments, cash discount
- Extra costs: maintenance deposit and contract fees; ROI calculator with rent, occupancy and yearly costs
- Compare up to three units, favourites, EGP / USD switch, deep link per unit, Arabic / English switch

## Engineering notes

- Filtering is a pipeline of small predicate stages (pipe-and-filter): adding a filter means adding one function.
- Results are paginated (9 at a time) and generated SVG art is memoised per unit.
- Stress test: with 5,600 listings, filtering takes about 5 ms, sorting about 3 ms and opening a unit about 19 ms.
- Compound names, prices and people are fictional.

## Performance and scale

The site is a single static file: no server, no database, no build step. Every visitor's browser does its own work, so traffic only reaches the CDN that serves the file (GitHub Pages), which is built for very high traffic. Orders and bookings go straight to WhatsApp, so there is no backend that can fail under load. Fonts load with `display=swap`, and state is kept in `localStorage` with safe fallbacks.

## Tech

HTML5, CSS3 (custom properties, grid, logical properties for RTL), vanilla JavaScript, inline SVG. No frameworks. Fonts from Google Fonts.

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
```

This is a demo project for my portfolio; the business, people and prices are fictional.

## Author

Mohamed Yehia · [GitHub](https://github.com/Mohamed-Yehia-ismail) · [LinkedIn](https://www.linkedin.com/in/mohamed-yehia-ismail)
