# Aniket Nutrition

Mobile-first local-first PWA for Indian food logging and nutrition tracking.

## Core rules
- The nutrition engine calculates values; natural-language logging only interprets food names and quantities.
- Unknown foods are never assigned nutrition values.
- Database values and user-entered custom values are explicitly distinguished.
- Daily history persists locally for 7-day averages and persistent-gap detection.
- Installable from Android Chrome when served over HTTPS.

## Run
Serve this directory from a web server (HTTPS is required for normal PWA installation/service-worker behavior), then open it in Chrome on Android and choose **Install app** / **Add to Home screen**.


## Data provenance
The current built-in food records are retained as reference estimates because their original source-record identifiers were not preserved in the supplied app. They are explicitly labelled as estimates in the UI. The next data pass should replace them with traceable IFCT 2017 and/or USDA FoodData Central records. IFCT 2017 is published by ICMR-NIN and covers 528 key foods; USDA FoodData Central provides downloadable, traceable food-composition datasets.


## v5 provenance model
Food records now carry `sourceType`, `sourceId`, `foodState`, `basis`, `ediblePortionPct`, and `servingGrams`. This makes it possible to replace reference estimates with traceable IFCT 2017 or USDA FoodData Central records without changing the calculation engine. Serving conversion supports grams, ml, kg/l, pieces, cups, tablespoons and teaspoons.

Sources: ICMR-NIN IFCT 2017 and USDA FoodData Central.


## v7 IFCT sync
The app can download the IFCT 2017 composition catalog from the @ifct2017/compositions package and cache it in localStorage for offline use. Each imported record keeps its IFCT food code as sourceId and missing nutrient fields remain null/unknown. The app does not infer missing B12 or other nutrients from other foods. Source attribution: ICMR-NIN IFCT 2017; package data derived from the published tables.
