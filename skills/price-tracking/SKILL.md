---
name: price-tracking
description: Track Amazon prices with Asin. Use when the user wants to find an Amazon product, follow its price, judge whether a price is good, see what dropped on their watchlist, set a target price or a drop alert, or see who sells a product and at what price.
---

# Track Amazon prices with Asin

Asin checks the price of each product on the user's watchlist on a schedule (daily on the free plan, down to every 5 minutes on paid plans), keeps every check as price history and emails the user when a price drops, reaches their target or the product is back in stock.

## Find and track a product

1. If the user names a product without an ASIN or a link, call `search_amazon` and confirm the right result with them before going further.
2. Call `track_product` with the ASIN or the Amazon link. It checks the price right away and returns it. Set `target_price` or `interval_minutes` only when the user asks for them.
3. If `last_error` is `product_not_found` and `found_on` lists other marketplaces, tell the user where the ASIN exists and offer to track it there.

## Answer questions about prices

- "Is this a good price?" or "how has it moved?": call `get_asin_history`. It's free and works on any ASIN, tracked or not. Compare the latest price with the lowest, highest and average price of the period.
- For a tracked product, `get_price_history` returns every check of that product.
- Questions about the whole watchlist: call `list_products` with `filter` set to `drops` (what got cheaper), `target` (what reached its target), `out_of_stock` or `attention` (anything wrong).
- "Who sells it?", Amazon's own price or a used one: call `get_offers` first, which is free. If `fetched_at` is null or old, `fetch_offers` reads Amazon for 1 credit: tell the user before calling it.

Prices are in the marketplace's currency. A `null` price means there was no offer at that check. Never invent a price that isn't in a tool's result.

## Credits and changes

Each scheduled price check costs 1 credit, and so do `check_product` and a new `fetch_offers` read. Say so before calling a tool that spends credits. `get_account` shows the plan and the remaining credits. When credits run out, tell the user they can see the plans at https://www.asin.dev/pricing.

`untrack_product` removes a product and its price history: ask the user to confirm first. Use `update_product` to change a target price, drop alerts, the check interval or to pause a product.

When a tool fails, its text ends with the error code in parentheses, such as `(product_limit)`. Explain the error in plain words.
