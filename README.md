# Integration_requirement

Shiprocket Button Auto Refresh on Shopify Variant Price Change
Overview

This script controls the visibility of the Shiprocket button on a Shopify product page based on the product’s price.

If price < ₹1500 → Shiprocket button is hidden

If price ≥ ₹1500 → Shiprocket button is shown

The main challenge addressed here is ensuring the button updates automatically when the user changes product variants — without requiring a page refresh.

Problem Statement

On Shopify product pages, variant changes update the price dynamically using JavaScript.
This causes two different behaviors:

✅ High → Low price change works

❌ Low → High price change does NOT refresh automatically

This happens because Shopify themes (like Dawn, Impulse, Motion, etc.) replace price DOM elements in multiple phases, causing normal event listeners and mutation observers to miss the final price update.


Root Cause

When a variant is selected:

Shopify replaces the price container

Then replaces the formatted price text

Sometimes updates variant JSON after DOM updates

As a result:

The script hides the Shiprocket button correctly (high → low)

But fails to re-show it (low → high), because the new price DOM is not detected in time