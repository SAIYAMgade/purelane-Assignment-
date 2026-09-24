# Purelane Shopify Theme Assignment

Purelane is a Dawn-based Shopify homepage implementation built from the supplied Purelane prototype. The final implementation uses Shopify-native Theme Editor settings and real Shopify product data where applicable.

## Sections

- Hero
- Purelane Shop / Product Grid
- Best-selling Combos
- Bundles
- Reviews Rail

Reusable Purelane snippets support product cards, combo cards, bundle tiers, and review cards. Section-specific styles live in dedicated assets where appropriate.

## Shopify setup

- Base theme: Shopify Dawn
- Final Shopify store: `saiyam-purelane.myshopify.com`
- Final submission theme: `Purelane Build`
- Final submission theme ID: `190446633327`

Shop uses real Shopify product data from the selected collection. Combos and Bundles use Shopify Theme Editor blocks with native `product_list` settings. Reviews use merchant-entered Theme Editor blocks; no review app integration is assumed.

The development catalog contains eight real Shopify products. Product cards handle sold-out products, products without images, and long product titles. The implementation includes responsive behavior, accessibility handling, reduced-motion handling, and CSS-only review marquee behavior.

Shopify Theme Check was run and the custom implementation introduced 0 new errors and 0 new warnings. Existing unrelated Dawn warnings remain documented in `BUILD_NOTES.md`.

## Local/development workflow

From the theme root:

```text
shopify theme check
```

The final submission theme can be pushed with:

```text
shopify theme push --store=saiyam-purelane.myshopify.com --theme=190446633327
```

Verify the CLI confirmation prompt names `Purelane Build` before confirming a push.

## Repository structure

```text
assets/       Section-specific and Dawn CSS/JavaScript assets
config/       Shopify theme configuration
layout/       Theme layouts
locales/      Theme translations
sections/     Shopify Liquid sections and schemas
snippets/     Reusable Liquid components
templates/    Shopify templates
BUILD_NOTES.md
AI_WORKFLOW.md
```

The prototype HTML is intentionally not committed to this repository. It was used as a visual source of truth during implementation.
