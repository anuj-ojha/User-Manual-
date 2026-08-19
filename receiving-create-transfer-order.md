# Create Transfer Order

Use the Receiving App to create a Transfer Order (TO) and initiate the movement of inventory from one facility to another.   

## Accessing the Create Transfer Order page

1. Log in to the Receiving App.
2. From the left-hand sidebar, select `Transfer Orders`.
3. Select the `Add (+)` icon at the bottom-right corner of the `Transfer Orders` page.
4. The `Create transfer order` page opens.

The page is divided into two sections:
- **Left panel**: Transfer order configuration (name, facility assignments, shipping method, and plan).
- **Right panel**: Product search and item list.

## Name the transfer order

- At the top of the left panel, locate the `Transfer name` field.
- Enter a clear, descriptive name in the `Name` field to help identify the transfer order later.

## Assign facilities

The `Assign` card contains the following fields:

### Product Store
- If your OMS manages multiple brands or product collections, select the appropriate `Product Store` from the dropdown.
- If only one store exists, it is selected by default and displayed as a label.

### Origin
- Select `Assign` next to `Origin` to open the facility selection modal.
- Search for the origin facility (the location that will ship the inventory) by name.
- Select the facility and confirm.

### Destination
- The `Destination` facility is automatically set to the current facility you are logged into.
- This field is read-only and cannot be changed from this page.

> **Note:** The origin and destination facilities cannot be the same. If you select an origin that matches the destination, the system will display an error when you attempt to create the order.

## Select shipping method

The `Shipping Method` card contains two fields:

### Carrier
- Select a shipping carrier from the `Carrier` dropdown.
- Available carriers are configured for your product store.

### Method
- After selecting a carrier, choose a shipment method from the `Method` dropdown.
- Available methods depend on the carrier selected.

## Plan the transfer lifecycle

The `Plan` card lets you define how the transfer order will be processed:

### Lifecycle
Choose the appropriate lifecycle based on how the transfer will be managed:

| Lifecycle | When to use |
| :--- | :--- |
| `Fulfill & Receive` | Store-to-store transfers managed entirely within OMS. |
| `Fulfill only` | Store-to-warehouse transfers where post-fulfillment is handled by an external WMS. |
| `Receive only` | Warehouse-to-store transfers where fulfillment is initiated externally and receipt is completed in OMS. |

### Ship Date
- Select `Select date` next to `Ship Date`.
- A date picker opens. Choose the estimated shipment date and confirm.

### Delivery Date
- Select `Select date` next to `Delivery Date`.
- A date picker opens. Choose the expected delivery date and confirm.

> **Note:** The delivery date cannot be earlier than the ship date.

## Add items to the transfer order

The right panel provides two methods to add products: **Scan** and **Search**. Toggle between these modes using the segment control at the top of the `Add items` card.

### Add items by scanning

1. Select the barcode icon to switch to `Scan` mode.
2. Place your cursor in the `Scan barcode` input field. The field shows the current barcode identifier type (for example, SKU or UPC).
3. Scan the product barcode using a connected scanner.
4. The scanned product appears below the input field with a confirmation icon.
5. If the product is already in the order, the system scrolls to the existing item instead of adding a duplicate.

**Scanner states:**
- **Scanner ready**: The input field is focused and ready for scanning. A green `start scanning` badge is displayed.
- **Scanner not focused**: A warning appears with a `Focus scanning` button. Select it to refocus the input field.
- **Product not found**: If the scanned barcode does not match any product, a `not found` message is displayed along with a `Search` button to try a keyword search instead.

> **Tip:** The barcode scanning identifier (SKU, UPC, etc.) can be changed from the `Settings` page.

### Add items by searching

1. Select the search icon to switch to `Search` mode.
2. Enter a keyword in the `Search` field. You can search by parent product name, SKU, or UPC.
3. The system displays matching products below the search field.
4. Select `Add to Transfer` to add the product to the order.
5. If more results are available, select `View more results` to open a full product search modal.

> Once a product is added, a green checkmark icon replaces the `Add to Transfer` button, indicating the product is already included in the order.

## Set item quantities

After adding items, each product appears in the item list below the `Add items` card:

- Each row displays the product image, name, and identification details.
- Enter the transfer quantity in the `Qty` field for each item.
- All items must have a valid quantity greater than zero before the order can be created.

### Remove an item
- Select the trash icon on the right side of an item row to remove it from the order.

## Create the transfer order

1. Review all the details:
   - Transfer name is entered.
   - Product store is selected.
   - Origin and destination facilities are assigned.
   - Carrier and shipping method are selected.
   - Lifecycle, ship date, and delivery date are configured.
   - At least one item is added with a valid quantity.
2. Select the **checkmark icon** (floating action button) at the bottom-right corner of the page.
3. The system validates the order. If any required field is missing or invalid, an error message is displayed at the top of the screen.
4. On successful creation, the system displays a confirmation message: `Order has been created and sent for admin approval`.
5. You are redirected to the `Transfer Orders` list page.

> The newly created transfer order will appear in `Created` status, allowing further modifications (such as adding items or editing quantities) before the order is approved.

## Validation rules

The following validations are enforced when creating a transfer order:

| Validation | Error message |
| :--- | :--- |
| No items added | `Please add atleast one item in the order.` |
| Transfer name is empty | `Please give some valid transfer order name.` |
| Missing product store, origin, destination, carrier, or method | `Please select all the required properties assigned to the order.` |
| Origin and destination are the same | `Origin and destination facility can't be same.` |
| Item quantity is zero or negative | `Order items must have a valid ordered quantity.` |
| Lifecycle not selected | `Please select transfer order lifecycle.` |

## Video walkthrough


