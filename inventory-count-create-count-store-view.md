# Create Cycle Count — Store View

The Create page in the Store view allows store managers to set up new cycle counts directly from the store.

## Accessing the Create page

1. Log in to the Inventory Count App with a store-level account.
2. From the bottom navigation bar, select the `Create` tab (identified by a `+` icon).
3. The `Create` page opens.

The Store view uses a bottom tab bar with the following tabs:

| Tab | Icon | Purpose |
| :--- | :--- | :--- |
| `Counts` | File tray | View assigned cycle counts for your facility |
| `Create` | Plus circle | Create a new cycle count |
| `Variance` | Shirt | Review item variances after counting |
| `Settings` | Gear | Configure app preferences |

> **Note:** The `Variance` tab is visible only if your user account has the required variance permission.

### Count name

- Locate the `Count name` field at the top of the form.
- Enter a clear, descriptive name for the cycle count.

> **Tip:** Use a naming format that helps your team quickly identify the count. For example: `Backroom-Shoes-Week33`.

### Facility

- Select the `Facility` chip to open the facility selection modal.
- Your current facility is pre-selected by default.
- Use the search bar to filter facilities by name or facility ID.
- Select the facility from the list and confirm.

> **Note:** In most cases, store users will keep the pre-selected facility (their own store). The ability to select a different facility is available for users with appropriate permissions.

### Count type

- Select the `Count type` dropdown.
- Choose one of the following count types:

| Count type | Description |
| :--- | :--- |
| `Directed count` | A targeted count of specific, pre-selected products. |
| `Hard count` | A full physical count of the entire facility. |

- `Directed count` is selected by default.

### Due Date

- Select `Add Date` next to `Due Date`.
- A date picker opens. Choose the date by which the count must be completed.
- Select `Done` to confirm.
- Only dates from today onwards can be selected.

### Start Date

- Select `Add Date` next to `Start Date`.
- A date picker opens. Choose the date when counting should begin.
- Select `Done` to confirm.
- This field is **optional**. If not set, the system defaults to the current date.

### Search for products

- Use the `Search products` search bar to find products by name, SKU, or product ID.
- Results appear as you type.

### Filter by tags

- Select the `Tags` chip to open a filter modal.
- Choose one or more tag values to narrow the product list.
- Select `Apply` to update the results.
- The chip label updates to reflect the selection (for example, `2 selected` or the tag name).

### Product list

Each product in the search results is displayed with the following details:

| Detail | Description |
| :--- | :--- |
| Checkbox | Select or deselect the product |
| Product image | Thumbnail of the product |
| SKU | Internal name or SKU |
| Product name | Product name or parent product name |
| Category | Primary product category |
| Product ID | System product identifier |

> **Note:** On smaller screens, the product list adapts to a mobile layout. The same information is available, but the columns may stack vertically for better readability.

### Select products

- Tap on any product row or its checkbox to select it.
- Selected rows are highlighted.
- The total number of selected items is displayed at the top-right (for example, `3 selected`).

### Select all products

- Use the `All` checkbox at the top of the list to select or deselect all visible products.
- If the total matching products exceed the loaded page, a `Select all [N]` button appears to include all matches.

> **Note:** A cycle count is limited to a maximum of 2,000 items. The system displays a warning if this limit is exceeded.

### Show selected only

- Enable the `Show selected only` toggle to view only the products you have already selected.
- This helps you review your selection before creating the count.
- The toggle is disabled when no products are selected.

## Create the cycle count

1. Review all the details:
   - Count name is entered.
   - Facility is selected.
   - Count type is chosen.
   - Due date is set.
   - Start date is set (if applicable).
   - At least one product is selected (for directed counts).
2. Select the `Create Cycle Count` button at the bottom-right corner of the page.
3. A confirmation dialog appears:
   - If a count with the same name already exists for the selected facility: `A count named "[name]" is already open for this facility, these items will be added to it. Continue?`
   - Otherwise: `Are you sure you want to create cycle count with [N] items?`
4. Select `Create` to confirm, or `Cancel` to go back.
5. On successful creation, a toast message is displayed: `The cycle count has been created successfully`.
6. The form resets, allowing you to create another count immediately.

> The newly created cycle count will appear under the `Counts` tab and is ready for the store team to begin execution.

## Validation rules

The following validations are enforced when creating a cycle count:

| Validation | Error message |
| :--- | :--- |
| Count name is empty | `Please enter count name` |
| No facility selected | `Please select a facility` |
| No due date selected | `Please select due date` |
| Start date is after the due date | `Start date cannot be after the due date` |
| No products selected | `Please select at least one item.` |
| Selection exceeds 2,000 items | `A count cannot have more than 2000 items` |

## Video walkthrough

`[📹 Video placeholder: Add a screen recording demonstrating the complete Create Cycle Count workflow from the Store view — including navigating to the Create tab via the bottom navigation bar, filling in count details, searching and selecting products, and submitting the count.]`

