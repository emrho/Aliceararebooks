# How to sell books on your website

Your "Books For Sale" section reads from a **Google Sheet**. You never touch the website code:
add a row and the book appears; tick **Sold** and it gets a Sold stamp.

---

## One-time setup (about 15 minutes)

### 1. Create the sheet
1. Go to **sheets.google.com** and start a blank spreadsheet. Call it something like *Aliceararebooks stock*.
2. In row 1, type these headings, one per column, exactly as written:

   | Title | Author | Year | Category | Condition | Description | Price | Photo | Buy Link | Sold |
   |---|---|---|---|---|---|---|---|---|---|

   (Or use **File → Import → Upload** with `books-template.csv` from this project, which has the headings plus an example row.)
3. Click the column letter above **Sold**, then **Insert → Checkbox**. Now each book gets a tick box.

### 2. Make a Stripe account (for taking payment)
1. Sign up at **stripe.com** and follow its steps to connect your bank account.
2. You'll make one payment link per book (see "Adding a book" below).

### 3. Publish the sheet to your website
1. In your sheet: **File → Share → Publish to web**.
2. Choose the tab with your books (e.g. *Sheet1*) and **Comma-separated values (.csv)**, then **Publish**.
3. Copy the link it gives you and **send it to Claude** (or whoever looks after the site). It gets pasted into the site once, and that's it.

> ⚠️ Anything on the published tab is public. Keep private notes (what you paid, where you bought it)
> on a **separate tab**. Only the tab you chose is published.

---

## Adding a book

1. **Photo:** upload it to Google Drive → right-click → **Share** → set to **Anyone with the link** → **Copy link**.
2. **Stripe link:** in the Stripe dashboard (or app) go to **Payment Links → New**:
   - Add a product with the book's title, price and photo.
   - Turn on **collecting the customer's shipping address**, and add a shipping rate if you charge postage.
   - Look for the option to **limit the number of payments** and set it to **1**, so the link stops working after one sale.
   - Create the link and copy it.
3. **Add a row** to your sheet:

| Column | What to put | Example |
|---|---|---|
| Title | The book's title | The History of the Decline and Fall of the Roman Empire |
| Author | Author (and translator if useful) | Edward Gibbon |
| Year | Year of this edition | 1838 |
| Category | Any short word. These become the filter buttons | History |
| Condition | Short condition note (shown on the card) | Half calf, rubbed; light foxing |
| Description | Longer notes, shown when someone taps the book | Armorial bookplate on front pastedown… |
| Price | Just the number. £ is added automatically | 85 |
| Photo | The Google Drive share link (or any https image link) | https://drive.google.com/file/d/… |
| Buy Link | Your Stripe payment link | https://buy.stripe.com/… |
| Sold | Leave unticked | ☐ |

Books without a photo get a drawn leather cover with the title in gold, so a photo is optional.

---

## Day to day

- **A book sells on your site:** Stripe emails you. Post the book, then tick **Sold**.
- **A book sells on eBay, Whatnot or Amazon:** tick **Sold** in the sheet *and* deactivate its Stripe link
  (Stripe → Payment Links → the link → Deactivate), so nobody can buy it twice.
- **Remove a book completely:** delete its row.
- **Change a price or description:** edit the cell. If you change the price, update the Stripe link too.

Changes usually show on the website **within about 5 minutes** (Google refreshes published sheets on its own schedule).
Sold books move to the end of the list with a red "Sold" stamp.
