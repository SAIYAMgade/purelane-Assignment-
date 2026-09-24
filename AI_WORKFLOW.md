# AI Workflow

## 1. How AI/Codex was used

Codex assisted with prototype inspection, Shopify/Dawn architecture analysis, Liquid implementation, scoped CSS, accessibility review, and Theme Check validation.

AI assistance was used as an implementation and analysis aid. The final code, Shopify configuration, browser testing, and product/content decisions were reviewed by the developer.

## 2. Prototype audit before implementation

The supplied `purelane-homepage.html` prototype was inspected section by section before implementation. The audits covered:

- Hero composition and product-stage behavior
- Shop grid and product-card structure
- Combo and bundle card layouts
- Reviews header, cards, duplicate marquee track, responsive rules, and reduced-motion behavior

Prototype hardcoded products, prices, ratings, names, quotes, and aggregate numbers were treated as visual reference rather than production data.

## 3. Small milestone strategy

The work was divided into focused milestones:

1. Hero structure and schema
2. Hero schema correction and pricing-tier validation
3. Hero token and spacing application
4. Hero prototype artwork and responsive behavior
5. Shop section shell and schema
6. Reusable product card
7. Shop/product-card integration
8. Combo architecture audit and shell
9. Combo visual styling and marquee-like rail treatment
10. Bundle architecture audit and shell
11. Bundle visual styling
12. Reviews architecture audit and shell
13. Reviews visual styling and CSS marquee
14. Documentation for final submission

Each milestone was kept narrowly scoped so implementation, validation, and review could happen before the next change.

## 4. Reusable Liquid snippets

The implementation created reusable snippets rather than repeating card markup inside sections:

- `purelane-product-card.liquid` handles product media, title, rating conditions, Dawn pricing, sold-out state, quick add, and product forms.
- `purelane-combo-card.liquid` renders dynamic combo products from block-level `product_list` settings.
- `purelane-bundle-tier.liquid` renders dynamic two-, three-, or five-product bundle tiers.
- `purelane-review-card.liquid` renders merchant-entered review content and accessible ratings.

The sections remain responsible for section-level settings, loops, schema, and layout composition.

## 5. Shopify-native editability priorities

The implementation prioritized Shopify-native Theme Editor settings and real Shopify product data:

- Shop uses a selected collection.
- Combos use block-level `product_list` settings.
- Bundles use block-level `product_list` settings.
- Reviews use repeatable merchant-entered blocks.
- Product badges use the `custom.card_badge` product metafield.
- Existing Dawn snippets and JavaScript are reused for pricing, product forms, quick add, and cart behavior.

The proposed combo metaobject approach was changed after reviewing the store’s Shopify Admin field picker, which did not expose the required Product reference type. Theme Editor `product_list` blocks were therefore used instead.

## 6. Manual review of AI-generated implementation

AI-generated code was reviewed for:

- Shopify Liquid and schema validity
- Theme Editor safety
- Real product-data usage
- No hardcoded product-specific production data
- Empty, sold-out, missing-image, and long-content states
- Accessibility semantics and focus behavior
- Section-scoped CSS and JavaScript
- Avoidance of changes to unrelated Dawn files

Where prototype content conflicted with production data requirements, it was intentionally omitted or replaced with merchant-editable settings.

## 7. Theme Check validation

`shopify theme check` was run after the implementation milestones.

The Purelane files introduced no new Theme Check errors or warnings. The repository retains nine pre-existing warnings in unrelated Dawn files. Those warnings were documented rather than modified because they were outside the assignment scope.

## 8. Browser and device QA

The completed sections were browser-tested at the requested responsive widths:

- 375px
- 390px
- 430px
- 768px
- 860px
- 1024px
- 1280px
- 1440px

QA included layout transitions, product imagery, horizontal rails, CTA behavior, keyboard focus, reduced motion, empty states, Theme Editor behavior, and marquee pause/duplication behavior where relevant.

No performance score, analytics result, or Lighthouse measurement was inferred from this testing.

## 9. Git commit strategy

Development was intentionally organized around small commits after focused milestones. The developer reviewed each milestone before committing it. Documentation changes are being prepared separately for final submission and have not been committed as part of this task.

No Git reset, rebase, force push, or destructive history operation was used for the documentation work.

## 10. Decisions reviewed or changed manually

Important decisions were not accepted blindly from the prototype or from initial AI suggestions:

- Hardcoded prototype product artwork was replaced with real Shopify product media.
- Hardcoded prototype pricing and savings were not presented as real bundle pricing.
- Metaobject-based combo data was replaced with Theme Editor `product_list` blocks after checking the actual Admin UI.
- Review-app integration was not claimed because no review app exists in the store.
- Aggregate review values default to blank rather than using prototype numbers.
- Reviews use merchant-entered blocks until a real review source is configured.
- Bundle and combo CTAs remain normal Shopify links instead of pretending to add multiple independent products to cart.
- Duplicated review marquee content is hidden from assistive technology and kept non-focusable.

The developer made the final decisions about scope, data sources, Shopify configuration, testing, and submission readiness.
