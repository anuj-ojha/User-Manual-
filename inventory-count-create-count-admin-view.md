# Create Cycle Count — Admin View

The Create Count page in the Admin view allows to set up new cycle counts and assign them to specific facilities. Once created, the assigned facility's store team can begin counting.

## Accessing the Create Count page

1. Log in to the Inventory Count App with an admin-level account.
2. From the left-hand sidebar, select `Create count`.
3. The `Create` page opens.

## Required permissions

To access the Create Count page, users must have one of the following permissions:

- `COMMON_ADMIN`
- `INV_COUNT_ADMIN`
- `INVCOUNT_APP_VIEW`

## Fill in the count details

### Count name

- Locate the `Count name` field at the top of the form.
- Enter a clear, descriptive name for the cycle count.
- This field is **required**. An error message `Please enter count name` is displayed if left empty.

### Facility

- Select the `Facility` chip on the right side of the `Facility` row.
- A facility selection modal opens.
- Use the search bar to filter facilities by name or facility ID.
- Select the target facility from the list by clicking the radio button.
- The modal closes and the selected facility name is displayed on the chip.

### Count type

- Select the `Count type` dropdown.
- Choose one of the following count types:

| Count type | Description |
| :--- | :--- |
| `Directed count` | A targeted count that includes only specific, pre-selected products. Store associates count only the items that appear in the directed list. |
| `Hard count` | A comprehensive, facility-wide count. Store associates count every product they encounter, whether or not it is in the system. |

- `Directed count` is selected by default.

### Due Date

- Select `Add Date` next to `Due Date`.
- A date picker opens. Choose the date by which the count should be completed.
- Select `Done` to confirm.
> The date picker only allows selecting dates from today onwards.

### Start Date

- Select `Add Date` next to `Start Date`.
- A date picker opens. Choose the date when the store team is expected to begin counting.
- Select `Done` to confirm.
- This field is **optional**. If not set, the system defaults to the current date.

> **Note:** Both dates are interpreted in the facility's local timezone. This ensures that store teams see the correct dates regardless of the administrator's location.

### Search for products

- Use the `Search products` search bar to find products by name, SKU, or product ID.
- Products matching the search term are displayed in a list below.

### Filter by tags

- Select the `Tags` chip to open a facet filter modal.
- Choose one or more tag values to narrow down the product list.
- Select `Apply` to update the results.
- The chip label updates to show the number of selected tag values (for example, `3 selected`) or the specific tag name if only one is selected.

### Product list columns

Each product row displays the following information:

| Column | Description |
| :--- | :--- |
| Checkbox | Select or deselect the product for inclusion in the count |
| Product image | Thumbnail of the product |
| SKU | Internal name or SKU of the product |
| Product name | Product name or parent product name |
| Category | Primary product category |
| Product ID | System product identifier |

### Select products

- Click on any product row or its checkbox to select it for the count.
- Selected rows are highlighted.
- The selection count is displayed at the top-right of the list (for example, `5 selected`).

### Select all products

- Use the `All` checkbox at the top of the list to select or deselect all currently visible products.
- If the total number of matching products exceeds the loaded page, a `Select all [N]` button appears. Select it to include all matching products across all pages.

> **Note:** A cycle count is limited to a maximum of 2,000 items. If you attempt to select more, the system displays a warning: `A count cannot have more than 2000 items`.

### Show selected only

- Enable the `Show selected only` toggle to display only the products that have already been selected.
- This is useful for reviewing your selection before submitting the count.
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
   - If a count with the same name already exists for the selected facility, the message reads: `A count named "[name]" is already open for this facility, these items will be added to it. Continue?`
   - Otherwise, the message reads: `Are you sure you want to create cycle count with [N] items?`
4. Select `Create` to confirm, or `Cancel` to go back.
5. On successful creation, a toast message is displayed: `The cycle count has been created successfully`.
6. The form resets, allowing you to create another count immediately.

The newly created cycle count will appear under the `Assigned` tab in the Cycle Count app, and the assigned facility's store team can begin execution.

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

`[📹 Video placeholder: Add a screen recording demonstrating the complete Create Cycle Count workflow from the Admin view — including navigating to the Create count page via the sidebar, filling in count details, searching and selecting products, and submitting the count.]`

