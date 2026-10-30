# Counter token

A one-file order screen for the counter. Pick items, print a token, next order.

Open `index.html` in Chrome. There is nothing to install, no server and no
internet needed — it is a single HTML file.

## How it works

- Tap an item to add it. Tap again for a second. The card turns orange and
  shows the count.
- Search and press Enter to add an item without hunting for it, which is
  faster once the staff know the menu.
- `−` and `+` on the bill change a quantity. Going below one removes the line.
- **Print token** sends an 80mm slip to the printer, then clears the screen and
  advances the number, ready for the next customer.

## The token number

Starts at 1 each morning and goes up by one every time a token is printed, so
the number on the slip always means "nth order today".

It is stored in the browser, which means:

- **Use the same browser on the same machine.** Opening the file on a second
  device starts its own count from 1.
- Refreshing, closing the tab or restarting the machine is fine — the number
  is remembered.
- "Clear" does **not** use up a number. A token is only taken when one is
  actually printed, so an abandoned order leaves no gap in the day's sequence.

## Changing things

Everything you would want to change sits at the top of the `<script>` block:

- `SHOP` — the name printed on the slip
- `GST_RATE` — currently `0.05` for 5%
- `MENU` — the items, as `['Name', price]` inside their category

**One price is missing.** `Red Rice Puttu` is listed on the menu board with no
price, so it is in here as `0` and the card shows `price?`. Fill in the real
number when you have it.

Prices are the board's own, exclusive of GST, and the GST line on the slip is
calculated at 5%. Parcel charges are typed in per order.

## Printing

Made for an 80mm thermal roll. In the browser's print dialog choose the
thermal printer and set margins to None; the page sizes itself.

Any printer works — on A4 the slip prints at the top of the sheet.
