# Purelane Shopify Build Notes

## 1. Project overview

Purelane is a production-oriented Shopify homepage implementation built for a Dawn theme. The work ports the supplied Purelane homepage prototype into merchant-editable Shopify sections while using real Shopify product data wherever products are displayed.

The five completed sections are:

1. Hero
2. Shop / Product Grid
3. Best-selling Combos
4. Bundles
5. Reviews Rail

## 2. Shopify setup

- Base theme: Shopify Dawn
- Store workflow: local theme files are validated with Shopify Theme Check and pushed to an explicitly targeted Shopify theme for browser testing and final submission.
- Store: `saiyam-purelane.myshopify.com`
- Final submission theme ID: `190446633327`
- Final submission theme name: `Purelane Build`

The prototype HTML is a visual reference only and is intentionally not part of the repository.

## 3. Architecture

Sections are implemented as Liquid section files with JSON schema for Theme Editor configuration.

Reusable Purelane snippets:

- `snippets/purelane-product-card.liquid`
- `snippets/purelane-combo-card.liquid`
- `snippets/purelane-bundle-tier.liquid`
- `snippets/purelane-review-card.liquid`

Section-specific stylesheets:

- `assets/section-purelane-shop.css`
- `assets/section-purelane-combos.css`
- `assets/section-purelane-bundles.css`
- `assets/section-purelane-reviews.css`

The Hero implementation keeps its section-scoped styling and behavior in `sections/hero.liquid`.

Shop product data comes from the selected Shopify collection. Combo and bundle products come from block-level Shopify `product_list` settings. Review content comes from merchant-entered review blocks.

Existing Dawn components are reused for product pricing, product forms, quick add, cart behavior, responsive images, and rating presentation where applicable.

## 4. Merchant editability

### Hero

- Headline and accent text
- Description
- Primary and secondary CTA labels and links
- Repeatable badges
- Pricing-tier blocks with editable labels, prices, compare-at prices, and savings labels

### Shop

- Collection
- Product count
- Kicker, heading, and description
- Ratings, product badges, secondary image, image ratio, and quick-add options

### Combos

- Repeatable combo blocks
- Combo title and description
- Shopify `product_list`
- Badge label
- Featured state
- CTA label and link
- Fine print

### Bundles

- Up to three tier blocks
- Tier label
- Shopify `product_list` with up to five products
- Derived product count with editable label text
- Description and richtext benefits
- Featured state
- CTA label and link
- Fine print

### Reviews

- Repeatable review blocks
- Review title and quote
- Reviewer name
- Product/category label
- Optional rating, verification, avatar, and date
- Optional aggregate display fields
- Marquee enable/disable setting

## 5. Data model decisions

- Shop uses real Shopify products from a merchant-selected collection.
- Combos use Theme Editor blocks with Shopify `product_list` settings.
- Bundles use Theme Editor blocks with Shopify `product_list` settings.
- Reviews use Theme Editor blocks with merchant-entered content.
- Product-card badges use `product.metafields.custom.card_badge` when populated.
- Product pricing is delegated to Dawn’s `snippets/price.liquid` where product-card pricing is shown.
- No review app integration is claimed or assumed. Aggregate review fields remain optional and blank-safe.
- No fake combined bundle prices or add-all-products cart behavior were introduced.
- Native Shopify bundle products can be connected later when real bundle pricing and inventory are available.

## 6. Edge cases handled

- Sold-out products show a clear unavailable state and do not use a normal add-to-cart submission.
- Products without images receive a placeholder treatment.
- Long product titles and review content wrap naturally.
- Missing optional review fields are omitted cleanly.
- An empty review section has a safe Theme Editor state.
- Empty or missing CTA links use safe fallbacks where defined.
- Combo and bundle product counts are derived from selected products.
- Responsive layouts were built for narrow mobile through wide desktop widths.
- Reduced-motion behavior disables or bypasses nonessential motion.
- Duplicate review content is marked hidden from assistive technology in the duplicated marquee track.

## 7. Accessibility considerations

- Section headings use unique section-scoped IDs.
- Product and CTA links use semantic anchors.
- Product images use Shopify media alt text or product-title fallbacks.
- Sold-out states are visible and included in accessible labels where applicable.
- Review ratings include accessible “Rated X out of 5” text.
- Decorative stars, checkmarks, plus signs, and duplicate review content are hidden from assistive technology as appropriate.
- Focus-visible styles are preserved or scoped to each Purelane section.
- No custom carousel creates a keyboard trap.
- Reduced-motion preferences are respected.

## 8. Performance considerations

- Shopify responsive image filters and lazy loading are used for product and review media.
- No third-party libraries were added.
- Existing Dawn product, cart, quick-add, and rating infrastructure is reused.
- Marquee behavior is CSS-based.
- Section-specific CSS is kept separate from global Dawn CSS.
- No untested performance scores or Lighthouse measurements are reported.

## 9. Theme Check validation

`shopify theme check` was run locally.

The Purelane section and snippet files introduced no new errors or warnings. The repository still reports nine pre-existing warnings in unrelated Dawn files, including warnings in layout, main product/search/article sections, facets, and an existing quick-order snippet.

Those unrelated warnings were not changed as part of this assignment.

## 10. Browser QA performed

The completed sections were browser-tested at the required responsive widths, including:

- 375px
- 390px
- 430px
- 768px
- 860px
- 1024px
- 1280px
- 1440px

Testing covered responsive transitions, horizontal rails, card sizing, CTA placement, product imagery, focus behavior, reduced motion, Theme Editor-safe empty states, and duplicate section behavior where applicable.

## 11. Known limitations and intentional decisions

- Prototype-only product artwork was replaced with real Shopify product media.
- Prototype prices and savings are not treated as production bundle prices.
- Combos and bundles do not automatically add multiple independent products to cart.
- Real native Shopify bundle products are required for authoritative combined pricing, inventory, and bundle checkout.
- Reviews are merchant-entered because no review app is configured.
- Aggregate review numbers remain optional and are not derived or invented.
- Prototype products that do not exist in the development catalog were not fabricated.

## 12. Development theme information

Final Shopify store: `saiyam-purelane.myshopify.com`

Final submission theme: `Purelane Build`

Final submission theme ID: `190446633327`

Typical validation workflow:

```text
shopify theme check
shopify theme push --store=saiyam-purelane.myshopify.com --theme=190446633327
```

The theme name and ID should be verified in the Shopify CLI confirmation prompt before pushing. The push must always include the explicit `--theme` argument.
