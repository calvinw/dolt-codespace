# Try a Price Increase on a Branch

A boutique's manager wants to know: **what if we raised prices?** In a
spreadsheet you would copy the file (`prices_v2_FINAL.xlsx`) and hope nobody
mixes up the copies. In Dolt you make a **branch**: a separate copy of the
database where you can try a change without touching the real data, which
stays on the branch called `main`.

`boutique.sql` builds a small boutique database:

| Name | What it is |
|---|---|
| `products` (table) | 12 products, with `cost` (what the boutique pays) and `price` (what the customer pays) |
| `sales` (table) | 200 sales from January to March 2026: date, store, product and quantity |
| `category_summary` (view) | Units sold, revenue and profit for each category |
| `store_summary` (view) | Number of sales, revenue and profit for each store |
| `product_margins` (view) | Each product's cost, price, margin %, units sold and revenue |

A **view** is a saved query. It doesn't store numbers; it calculates them
from the tables every time you look at it. So the same view shows different
numbers on different branches.

## Before you start

1. Start `opencode` in the terminal.
2. If Dolt isn't installed in this codespace yet, give the agent the Step 1
   prompt from the [retail-orders](../retail-orders/README-retail-orders.md)
   exercise. (You'll need the Step 2 login prompt from there too, for Step 7
   below.)

Copy each prompt into OpenCode and press **Enter**. Read what the agent says
before you go on.

## Step 1: Build the Database

```default
Create a new Dolt database in a folder called dolt-branches/boutique. Load dolt-branches/boutique.sql into it, show me its tables and views, and commit it with the message "Create boutique database with three views".
```

## Step 2: Look at the Views on main

```default
Explain each of the three views in plain words. Then show me what each one shows right now, on the main branch.
```

Write down the total revenue and profit for each category. You will compare
them later.

## Step 3: Make a Branch

Pick one category (Dresses, Tops, Bottoms, Outerwear or Accessories) and a
price increase, for example 10%.

```default
Explain what a branch is. Then create a branch called price-increase and switch to it. Tell me which branch I am on.
```

## Step 4: Raise the Prices on the Branch

```default
On the price-increase branch, raise the price of every CATEGORY product by PERCENT. Show me exactly which rows changed, then commit it with a message that says what you changed.
```

## Step 5: Compare the Views

```default
Show me each of the three views on main and on price-increase, side by side, with the difference. Which numbers changed, which stayed the same, and why?
```

Think about it:

- Why did revenue go up but **units sold** stay the same?
- Which stores gained the most, and why those?
- What happened to the margin % of the products whose price went up?
- The views assume customers buy the same amount at the higher price. Is
  that realistic? What might really happen?

## Step 6: See Exactly What Changed

```default
Show me everything that is different between main and price-increase, and the commit history of each branch.
```

Notice that only a few rows in `products` changed, yet every report that uses
prices changed with them. In a workbook, you would have to make sure every
sheet and formula picked up the new prices.

## Step 7: Decide

You are the manager. Either **keep** the price increase or **reject** it.

To keep it:

```default
Merge the price-increase branch into main, then show me the category_summary view on main and the commit history of main.
```

To reject it, leave `main` as it is. Your branch stays as a record of the
idea.

Either way, put your database on DoltHub, with both branches. On DoltHub, go
to <https://www.dolthub.com/profile> and click **Create Database**. Name it
`boutique-branches`, make it **Public**, and click **Create**. Leave it empty.

```default
Add my DoltHub database YOUR-DOLTHUB-USERNAME/boutique-branches as the remote called origin, and push both the main and the price-increase branches to it.
```

On DoltHub, use the **branch** menu to switch between `main` and
`price-increase`, and open the views on each.

## What to Hand In

1. The link to your `boutique-branches` database on DoltHub, with both
   branches.
2. Short answers, in your own words:
   - Which category did you change, and by how much?
   - How did revenue and profit change for that category, and for the whole
     business?
   - Did you merge the price increase into `main` or not? Why?
   - Why is a branch safer than editing the real data, or copying a
     spreadsheet?
