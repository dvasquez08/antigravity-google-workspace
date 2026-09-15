````markdown
# Solo Meal Plan & Grocery Automation Agent

## Objective

Autonomously research 5 practical, single-portion (or 1–2 serving meal-prep) dinner recipes, verify community sentiment, fetch local weekly flyer deals in **_YOUR CITY HERE_** via Flipp's public search API, generate a formatted weekly Google Doc in Google Drive, log the recipes to Google Sheets, and dispatch a summary email.

---

## Execution Environment & Policies

- **Execution Mode:** 100% autonomous / unattended (`always-proceed`).
- **Target Location:** **_YOUR CITY SATE/PROVINCE_**(Postal Code: `POSTAL/ZIP CODE HERE`).
- **Store Preferences:** Prioritize "YOUR FAVORITE STORES HERE".

---

## Step-by-Step Workflow

### Step 1: Research 5 Single-Serving Recipes

- Search YouTube for 5 fast, flavorful dinner recipes scaled for 1 person (e.g., quick 15-minute stir-fries, single-skillet meals, minimal-dishes dinners, or batch-friendly recipes yielding exactly 1 dinner + 1 lunch leftover).
- Cross-reference with community feedback (e.g., Reddit `r/CookingForOne`, `r/EatCheapAndHealthy`, or creator comments) to confirm low food waste, minimal leftover fatigue, and realistic ingredient proportions.
- For each recipe, capture:
  - **Recipe Name**
  - **Prep & Cook Time**
  - **Portion Size:** 1 serving (or 1 serving + 1 leftover lunch)
  - **Food-Waste & Storage Notes** (how to freeze unused ingredients like half-cans or herbs)
  - **Clear Step-by-Step Cooking Instructions**
  - **YouTube Video Title and URL**

### Step 2: Consolidate the Grocery List

- Extract all ingredients across all 5 single-serving recipes.
- Deduplicate overlapping ingredients into a lean list of 6 to 10 core items (prioritize multi-use ingredients across recipes to minimize perishable waste).
- Omit standard pantry staples: tap water, basic cooking oil, salt, black pepper.

### Step 3: Grocery Pricing Lookup via Flipp Public API

- For each consolidated ingredient, query Flipp’s public search endpoint using a standard browser `User-Agent` header:
  ```text
  GET [https://backflipp.wishabi.com/flipp/items/search?q=](https://backflipp.wishabi.com/flipp/items/search?q=){INGREDIENT}&postal_code=A1A2B2 <== REPLACE THIS WITH YOUR POSTAL/ZIP CODE, ERASE THIS COMMENT TOO
  Header: User-Agent: Mozilla/5.0
  ```
````

- **CRITICAL PRICING RULES:**
  1. **Prioritize Sale Prices:** If an item has a discounted or “special” price, **ALWAYS** record the sale price (not the regular price).
  2. **Unit Normalization:** If the result is “3 for $5” or “2 for $4”, convert it to the **per-item unit price** (e.g., $1.67 each or $2.00 each). Do not show the bundle price.
  3. **No Results Handling:** If Flipp returns no results for an ingredient, state "No sale found" but still estimate a **reasonable local grocery price** (e.g., $2.50) to ensure the meal cost is calculable.
- Compile the weekly price findings into a clean Markdown table.

### Step 4: Compile the Weekly Shopping List

- Create the complete grocery list, including:
  - Item Name
  - Quantity Needed (scaled for 4 servings)
  - Best Sale Price Found (or estimated price if no sale)
  - Best Store (Superstore, No Frills, Walmart)

### Step 5: Generate Google Assets

- **Google Docs**: Generate a formatted Google Doc containing:
  - **Full Weekly Meal Plan**: All 5 recipes with instructions.
  - **Grocery Price Comparison**: The Markdown table with sale prices.
  - **Total Estimated Weekly Cost** (and cost per serving).
  - Save the Doc in your Google Drive folder `Recipes`.
- **Google Sheets**: Add rows to the catalog sheet (`FILE ID OR FILE URL`) with the recipe names, date, and the new Doc URL.
- **Email**: Dispatch a styled HTML summary email to the user containing the meal plan highlights, the total estimated cost, and a direct link to the Google Doc.

## Output Format

- **Google Doc**: Clean Markdown / Formatted Document.
- **Email**: HTML.
- **Sheets**: Tab-delimited or CSV row / Sheets API append.

## Quality Mandates

- All meal instructions must be **clear, simple, and scaled for 4 portions**.
- All pricing must reflect **current local weekly flyers** (via Flipp).
- Execution must be **100% unattended**.
