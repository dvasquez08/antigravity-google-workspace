# Toddler Meal Plan & Grocery Automation Agent

## Objective

Autonomously research 5 nutritious, toddler-approved meals, verify parent feedback, look up local weekly flyer deals in **_YOUR_CITY_HERE_** via Flipp's public search API, create a formatted weekly Google Doc in Google Drive, log the recipes to Google Sheets, and dispatch a summary email.

---

## Execution Environment & Policies

- **Execution Mode:** 100% autonomous / unattended (`always-proceed`).
- **Target Location:** **_YOUR_CITY_STATE/PROVINCE_** (Postal Code: `POSTAL/ZIP CODE HERE`).
- **Store Preferences:** Prioritize "YOUR FAVORITE STORES HERE".

---

## Step-by-Step Workflow

### Step 1: Research 5 Toddler-Approved Recipes

- Search YouTube for 5 popular, nutrient-dense toddler meals or finger foods (easy prep, hidden veggies, balanced protein/fiber).
- Cross-reference with parent feedback (e.g., Reddit `r/toddlerfood`) to verify kid acceptance and texture feasibility.
- For each recipe, capture:
  - **Recipe Name**
  - **Prep & Cook Time**
  - **Practical Parent Tips** (choking safety, freezing, texture adjustments)
  - **Clear Step-by-Step Cooking Instructions**
  - **YouTube Video Title and URL**

### Step 2: Consolidate the Grocery List

- Extract all ingredients across all 5 recipes.
- Deduplicate overlapping ingredients into a clean list of the top 8 to 12 core items.
- Omit basic pantry staples: tap water, basic cooking oil, salt, black pepper.

### Step 3: Grocery Pricing Lookup via Flipp Public API

- For each consolidated ingredient, query Flipp’s public search endpoint using a standard browser User-Agent header (via curl, fetch, or Python):
  ```text
  GET [https://backflipp.wishabi.com/flipp/items/search?q=](https://backflipp.wishabi.com/flipp/items/search?q=){INGREDIENT}&postal_code=A1A2B2 <===Replace  this placeholder, Postal/Zip Code Here And Erase This Comment too.
  Header: User-Agent: Mozilla/5.0
  ```
- **CRITICAL PRICING RULES:**
  1. **Prioritize Sale Prices:** If an item has a discounted or “special” price, **ALWAYS** record the sale price (not the regular price).
  2. **Unit Normalization:** If the result is “3 for $5” or “2 for $4”, convert it to the **per-item unit price** (e.g., $1.67 each or $2.00 each). Do not show the bundle price.
  3. **No Results Handling:** If Flipp returns no results for an ingredient, state "No sale found" but still estimate a **reasonable local grocery price** (e.g., $2.50) to ensure the meal cost is calculable.
- Compile the weekly price findings into a clean Markdown table.

### Step 4: Compile the Weekly Shopping List

- Create the complete grocery list, including:
  - Item Name
  - Quantity Needed
  - Best Sale Price Found (or estimated price if no sale)
  - Best Store (Superstore, No Frills, Walmart)

### Step 5: Generate Google Assets

- **Google Docs**: Generate a formatted Google Doc containing:
  - **Full Weekly Meal Plan**: All 5 recipes with instructions.
  - **Grocery Price Comparison**: The Markdown table with sale prices.
  - **Total Estimated Weekly Cost**.
  - Save the Doc in your Google Drive folder `Toddler Recipes`.
- **Google Sheets**: Add one row to the catalog sheet (`FILE ID OR FILE URL HERE`) with the date and the new Doc URL.
- **Email**: Dispatch a styled HTML summary email to the user containing the meal plan highlights, the total estimated cost, and a direct link to the Google Doc.

## Output Format

- **Google Doc**: Clean Markdown.
- **Email**: HTML.
- **Sheets**: Tab-delimited or CSV row.

## Quality Mandates

- All meal instructions must be **clear, simple, and toddler-safe**.
- All pricing must reflect **current local weekly flyers** (via Flipp).
- Execution must be **100% unattended**.
