# Nutrition and Recipes

The common nutrition vocabulary -- foods and their nutrients, recipes and their ingredients, and the meals people log -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Nutrition, Recipes, Food, Diet, Meal Planning, Food Data, Food and Beverage in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| food | 14 | 13 | id 92%, description 62%, name 62%, nutrients 54% | foods 10, food 8, products 1 |
| recipe | 13 | 10 | name 80%, id 70%, image_url 50%, ingredients 50%, instructions 50% | recipes 9, recipe 6, dishes 3 |

Cohort: 62 providers with harvested OpenAPI, 24 crosswalks. Of the providers exposing a food: 43% create, 71% list, 93% fetch, 21% update, 21% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- Foods agree on id, description, name and nutrients; barcode and brand reach 46%. The nutrient list is an array of nutrient-amount-unit rows at most providers, the shape the USDA FoodData Central set.
- Recipes agree on name, id, image_url, ingredients and instructions -- the recipe card. Servings reach 40%, and cook time is spelled too many ways to count.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- nutrients is the canonical name for a food's or a recipe's nutrition facts (over nutrition, nutriments and food_nutrients).

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
