# Configure threshold and safety stock

HotWax Commerce Order Management System (OMS) provides inventory buffers to prevent overselling and protect store inventory. In the Order Routing App, you can configure these buffers using threshold and safety stock rules.

While both features reduce the amount of inventory available to promise (ATP) to online orders, they operate at different scopes and solve different business problems.

## Threshold

A threshold is the number of units held back from a specific online channel to ensure inventory is not oversold. 

Thresholds apply at the channel level. When you set a threshold for a channel, the OMS subtracts the threshold value from the total available inventory. The resulting ATP is then synced to that specific channel.

For example, if a store has 20 units of a product and you configure a threshold of 5 for your Shopify channel, the channel will display 15 units as available. The remaining 5 units are protected for walk-in customers or other sales channels.

### Client problems and solutions for threshold

* **Prevent overselling on high-velocity items:** 
  * **Problem:** During flash sales or product drops, items sell out faster than the inventory can sync between the POS, the OMS, and the eCommerce channel, leading to cancelled orders and unhappy customers.
  * **Solution:** Configure a high threshold for products tagged as "high-velocity" or "flash-sale" to ensure the eCommerce channel stops taking orders early, leaving a safe buffer to absorb sync delays.
* **Managing channel-specific buffers:** 
  * **Problem:** A retailer sells on both a primary website (Shopify) and a marketplace (Amazon). Amazon heavily penalizes sellers for canceled orders due to stockouts, while Shopify is more forgiving.
  * **Solution:** Create two separate threshold rules. Set a higher threshold (e.g., 5) for the Amazon channel to ensure zero cancellations, and a lower threshold (e.g., 2) for the Shopify channel to maximize sales.
* **New store or region protection:** 
  * **Problem:** When onboarding a new store or opening a new regional fulfillment center, inventory accuracy is often unverified and fulfillment operations are untested.
  * **Solution:** Apply a high threshold to restrict the new store's inventory exposure on online channels until operations stabilize and counts are verified.
* **Seasonal adjustments for walk-in traffic:**
  * **Problem:** During high-traffic periods like the holiday season, physical stores see a massive increase in walk-in customers.
  * **Solution:** Retailers can temporarily increase threshold values to reserve more inventory for in-store shoppers, then revert the rules after the peak season.

### Create a threshold rule

1. Open the Order Routing App and navigate to the `Threshold` page.
2. Click `Create threshold rule`.
3. Enter a descriptive rule name.
4. Enter the `Threshold` value. This must be a positive integer.
5. Select the inventory channels this rule applies to. You can select specific channels or toggle `Select all channels`.
6. (Optional) In the `Products` section, add product tags or features to include or exclude specific items from this rule.
7. Click `Save`.

## Safety stock

Safety stock is a buffer of inventory reserved per facility or facility group to ensure it is never promised to any online order, regardless of the channel.

Safety stock applies at the facility group level. When the routing engine evaluates a facility for fulfillment, it treats the facility's inventory as reduced by the safety stock value.

For example, if a warehouse has 50 units of a product and you configure a safety stock of 10 for your warehouse facility group, the routing engine considers only 40 units available for order allocation.

### Client problems and solutions for safety stock

* **Accounting for inventory inaccuracies (shrinkage):**
  * **Problem:** Store associates frequently complain about being asked to fulfill orders for the last item on the shelf. The last item is often damaged, missing, or stolen (shrinkage), causing the store to reject the order.
  * **Solution:** Configure a safety stock of 1 or 2 across all store facilities. This prevents the routing engine from ever targeting the "last unit" on the shelf, drastically reducing order rejection rates and fulfillment delays.
* **Protecting BOPIS inventory:**
  * **Problem:** A retailer offers Buy Online Pick Up In Store (BOPIS). If Ship From Store (SFS) orders drain all the inventory at a location, local customers cannot place BOPIS orders.
  * **Solution:** Set a safety stock level for retail stores. This ensures a baseline of inventory is preserved at the physical location, keeping it available for walk-in purchases and local BOPIS pickups.
* **Facility-level operational reserves:**
  * **Problem:** Warehouses need to hold back inventory for wholesale orders, emergency replacements, or returns exchanges that bypass the standard eCommerce order flow.
  * **Solution:** Configure a safety stock rule specifically targeting the warehouse facility group to reserve a dedicated pool of units.
* **Protecting high-value items:**
  * **Problem:** Expensive electronics or luxury goods need tighter inventory controls and should not be aggressively brokered if stock is low.
  * **Solution:** Use product tag filters in the safety stock rule to apply a buffer only to high-value items, leaving the rest of the catalog unaffected.

### Create a safety stock rule

1. Open the Order Routing App and navigate to the `Safety stock` page.
2. Click `Create safety stock rule`.
3. Enter a descriptive rule name.
4. Enter the `Safety stock` value. This must be a positive integer.
5. In the `Facilities` section, select the facility groups to include. The rule will apply to all facilities within these groups.
6. (Optional) Select facility groups to exclude.
7. Click `View impacted facilities` to verify which specific locations are affected by your selections.
8. (Optional) In the `Products` section, add product tags or features to include or exclude specific items.
9. Click `Save`.

## Brokering safety stock

Brokering safety stock is an inventory filter configured directly within an order routing rule. Unlike standard safety stock rules, it does not modify the stored inventory values. Instead, it sets a minimum inventory floor that a facility must exceed for the routing engine to consider it eligible for fulfillment.

For example, if you configure a brokering safety stock of 5, the routing engine will only route orders to facilities that have an ATP greater than 5 units.

### Client problems and solutions for brokering safety stock

* **Preventing order rejection cascades:**
  * **Problem:** If an order is routed to a store with only 1 unit available, the store may reject it due to stock inaccuracy. The engine then routes it to the next store with 1 unit, which also rejects it, causing a cascade of delays.
  * **Solution:** Create a primary routing rule with a brokering safety stock of 3. The engine will prioritize stores with a deeper depth of inventory, significantly reducing the chance of rejection and increasing fulfillment speed.
* **Balancing fulfillment loads:**
  * **Problem:** Retailers want to fulfill orders from stores, but don't want to completely drain a store's inventory if a warehouse has plenty of stock.
  * **Solution:** Set up a routing sequence where the first rule attempts to route to stores with a brokering safety stock of 5. If no store has 5+ units, the next rule routes to the warehouse. This preserves shallow store inventory while prioritizing stores with excess stock.

### Configure brokering safety stock

1. Open the Order Routing App and navigate to a routing rule within a routing group.
2. In the rule editor, locate the `Inventory filters` section.
3. Click the `Safety stock` chip.
4. Enter the minimum inventory value required.
5. Click `Save` to update the routing rule.

## Shipment threshold check

The shipment threshold check is an inventory filter that evaluates the monetary value of a potential shipment. If an order is split across multiple facilities, the routing engine calculates the subtotal of the items assigned to each facility. If a shipment's subtotal is below the configured threshold, the routing engine rejects the allocation and evaluates the next rule.

This check only applies to partial assignments where items are split across multiple locations.

### Client problems and solutions for shipment threshold

* **Avoiding unprofitable split shipments:**
  * **Problem:** A customer orders a $150 jacket and a $5 pair of socks. The jacket is fulfilled by Store A, but the socks are only available at Store B. Shipping the socks alone from Store B costs $8, resulting in a net loss on that item.
  * **Solution:** Set a shipment threshold check of $15 in the routing rule. The engine will reject the split shipment to Store B, preventing the unprofitable fulfillment. It will instead evaluate the next rule to find a location that can fulfill both items together, or leave the socks unfulfilled until a better location is found.
* **Consolidating packaging:**
  * **Problem:** Splitting orders excessively leads to higher packaging costs and a poor unboxing experience for the customer.
  * **Solution:** The shipment threshold forces the routing engine to bypass locations that can only fulfill a tiny fraction of the order, encouraging the system to consolidate the order into fewer, larger shipments.

### Configure shipment threshold check

1. Open the Order Routing App and navigate to a routing rule within a routing group.
2. In the rule editor, locate the `Inventory filters` section.
3. Click the `Shipment threshold check` chip.
4. Enter the minimum monetary value required for a shipment.
5. Click `Save` to update the routing rule.
