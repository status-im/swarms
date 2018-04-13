## SDK Iterations


### Protocol messages

[New protocol spec](https://docs.google.com/document/d/1Qh2h07T_qepzEJ7IytmxwIdQAOsGHrvhXwZxuZtbwgc/edit#) clearly defines all message types with examples. It's based on [transit-format](https://github.com/cognitect/transit-format), so it makes sense to evaluate its [go implementation](https://github.com/russolsen/transit)

Use cases:

### General
#### [ ] Message

##### Parameters:
  - content: the content of the message (a map or a string for now)
  - content-type: the content-type of the message
  - message-type: the type of the message
  - to-clock-value : the clock of the sender for message ordering
  - timestamp: the timestamp of message

*Where does the destination/s of the message is defined?*


#### Private groups

##### [ ] NewGroupKey

- [ ] GroupAdminUpdate
- [ ] GroupLeave

#### Contact management
- [ ] NewContactKey
- [ ] ContactRequest
- [ ] ContactRequestConfirmed
- [ ] ContactUpdate

#### Not needed for first iteration
- [ ] Seen


##### Message


### Define final SDK UI based on different messages
