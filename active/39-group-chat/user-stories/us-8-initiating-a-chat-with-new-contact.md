# User Story 7: Initiating a Chat with a New Contact

## Description

*User A* wants chat with *User B* as a new contact.

## Trigger

*User A* wants to send a message to *User B*. *User B* is not in the
contact list of *User A*.

## Actors

- *User A*
- *User B*

## Pre-Condition

*User A* views chat list not containing *User B*.

## Post-Condition

*User A* sent a message to *User B* and *User B* is added to the
chat list.

## Flow

- *User A* selects the plus icon for adding a new tab.
- Here she has two choices of adding *User B* by selecting
  the according menu entry:
  - She can enter the public key of *User B*
  - She can scan the QR code of *User B*
- A field for entering a text appears.
- *User A* enters her message and selects the icon for sending
  a message.
- The message is sent to *User B*.
- *User A* presses the icon to return to the Status view.
- Chat with *User B* is listed on the top.

## Remarks

- Question: Does pressing *Return* send a message too or does
  it adds a line break?
- Idea: Alternatively to scan QR via camera scan it from an
  existing photo. This way QR codes can quickly be captured
  outside of Status and later added as a contact.