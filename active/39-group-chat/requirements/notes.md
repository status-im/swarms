# Notes

- A format / schema for moderation rules must be defined.
- A standard rules interface for smart contracts must be defined.
- A smart contract that must:
  - Allow a caller to burn any ERC20 token.
  - Allow a caller to label burn amounts.
  - Return burn amounts given a token address, user address, and an optional label.
- A moderation settings UI must exist where the user may configure:
  - Blocked users.
  - Filtered phrases.
  - The address of a smart contract to call.
  - Burn amount required.
- UserA must be able to block a UserB from UserB's profile.
- Messages are evaluated against the moderation rules before they are rendered, aborting render where necessary.
- Moderation rules must persist between sessions.
- Chat group settings UI must:
  - Display the user's burn amount for that channel.
  - Allow users to burn tokens for that channel.