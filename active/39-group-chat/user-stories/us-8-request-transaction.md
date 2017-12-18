# User Story 8: Request Transaction from Chat Partner

## Description

*User A* requests transaction from *User B*.

## Trigger

*User A* wants to request an amount of token from *User B*.

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
- Beside the text field the menu for requesting a transaction appears.
- *User A* selects the menu entry `/request`
- A menu listing the supported currencies appears.
- The user selects the wanted currency.
- The text field displays the request command as well as the currency.
- It expects *User A* to enter the amount.
- After entering it *User A* presses sent.
- A confirmation dialog appears and she can select to send
  the request.

## Remarks

- Question: Are the currencies hard coded or can the user
  configure them?
- Clearing: Demo shows entering the amount in text field
  but also entering it in the follow-up dialog. Both ways possible?