# Message Queues
- A Queue server runs independently
- it is tasked with routing events and messaging between clients.
```
Any connected client can “publish” a message into the server.
Any connected client can “subscribe” to receive messages by type.
```
- The Queue server has the ability to see which events they are subscribed to.
- It is tasked with receiving any published message and then distributing it out to clients. 
- Ensure that subscribed clients can “catch up” and pull down any missing messages

### What is a message?
- A message is a package of information, categorized by queue and event
- `queue` - Which general bucket does this message belong
    - i.e. “Database Events”, “Filesystem Events”, “Network Events”, etc
- `event` - What event has happened
    - i.e. “delete, add, update, connection lost, error”, etc.
- `payload` - data associated with the event
    - i.e. “record id, record information, error text”, etc.
    
### Real Time 
- In some cases, messages are simply brokered by the server. 
- they arde processed and immediately broadcast out to subscribers. 
- If lost connection with the server, any messages will be missed by the client.

### Queued Messaging
- A true “Queue” will keep track of the delivery status of every event/message. 
- Any broadcast that is not received by a subscriber will remain “in the queue” until it can be delivered.
