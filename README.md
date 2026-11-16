# Asin

![Asin](./assets/logo.png)

Asin tracks Amazon prices for you. Search Amazon, add a product to your watchlist by ASIN or link, and Asin checks its price on a schedule, keeps every price as history and emails you when it drops, reaches your target or is back in stock. Ask how a price has moved before you buy, which tracked products got cheaper, or who sells a product and at what price. It works on 11 Amazon marketplaces: the US, UK, Germany, France, Italy, Spain, Canada, Japan, Brazil, Mexico and India.

## What you need

An Asin account. Sign up for free at [asin.dev](https://www.asin.dev): the free plan tracks up to 50 products, checked daily. You sign in to Asin the first time you use the plugin.

## What you can ask

- "Which products on my watchlist dropped in price?"
- "Is now a good time to buy the Kindle Paperwhite? Check its price history."
- "Track this Amazon product and email me when it goes under $100."
- "Who sells this product, and what's Amazon's own price?"
- "Pause the products I haven't looked at in a month."

## What's inside

- **Asin connector**: Asin's MCP server at `https://www.asin.dev/api/mcp`. It searches Amazon, manages your watchlist and reads price history and offers.
- **price-tracking skill**: teaches Claude when to use each tool, which ones spend credits, and to confirm before removing a product.

## Data and privacy

The plugin talks only to Asin's server at `www.asin.dev`. It sends what you ask Claude to look up or change: search keywords, ASINs and Amazon links, target prices and alert settings. Asin stores your watchlist and its price history in your account; it never sees your Amazon account or your orders. Read the [privacy policy](https://www.asin.dev/privacy-policy) and the [terms](https://www.asin.dev/terms).

Each price check of a tracked product costs 1 credit, and a product checked daily uses about 30 credits a month. Claude tells you before running a tool that spends credits.

## Support

Write to [contact@asin.dev](mailto:contact@asin.dev) or visit [asin.dev/support](https://www.asin.dev/support). Full documentation: [asin.dev/docs](https://www.asin.dev/docs).
