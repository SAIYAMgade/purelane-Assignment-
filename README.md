# Purelane Shopify Theme Assignment

Purelane is a Dawn-based Shopify homepage implementation built from the supplied Purelane prototype. The five completed sections use Shopify-native Theme Editor settings and real Shopify product data where applicable.

## Sections

- Hero
- Purelane Shop / Product Grid
- Best-selling Combos
- Bundles
- Reviews Rail

Reusable Purelane snippets support product cards, combo cards, bundle tiers, and review cards. Section-specific styles live in dedicated assets where appropriate.

## Shopify setup

- Base theme: Shopify Dawn
- Development store: `saiyam-purelane.myshopify.com`
- Development theme: `Development (14080d-sam)`
- Development theme ID: `190431265135`

Shop products use real products from the selected collection. Combos and bundles use Theme Editor blocks with Shopify `product_list` settings. Reviews use merchant-entered blocks; no review app integration is assumed.

## Local/development workflow

From the theme root:

```text
shopify theme check
```

The development theme can be pushed with:

```text
shopify theme push --store=saiyam-purelane.myshopify.com --theme=190431265135
```

Verify the CLI confirmation prompt names `Development (14080d-sam)` before confirming a push.

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
