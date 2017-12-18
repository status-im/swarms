# User Story 8: Send Transaction to Chat Partner

## Description

*User A* sends a transaction to *User B*.

## Trigger

*User A* wants to send an amount of token to *User B*.

## Actors

- *User A*
- *User B*

## Pre-Condition

*User A* has *User B* in her contact list.

## Post-Condition

Request of the wanted amount of token is sent from *User A*
to *User B*.

## Flow

- *User A* selects *User B* from her list of contacts.
- She selects the icon for new message.
- Beside the text field the menu for sending a transaction appears.
- *User A* selects the menu entry `/send`
- A menu listing the supported currencies appears.
- The user selects the wanted currency.
- The text field displays the send command as well as the currency.
- It expects *User A* to enter the amount.
- After entering it *User A* presses sent.
- The transaction data with recipient, currency, and amount is
  shown and the user selects "Sign Transaction".
- *User A* signs the transaction.

## Remarks

- Question: How does the user sign the transaction?
