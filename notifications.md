# EIP - Selective Notification

*Not designed for messaging, p2p, etc... This is basically the equivalent of a newsletter in your inbox (gross, I know, but crypto is not flooded by spam)*

An lightweight notification system for teams aiming to communicate with their holders. Intended to provide the flexibility for notifying specific wallets based on balance or age of asset deposited into the wallet, etc...

DAO's currently have a difficult way of communicating on channel that's available **to all** holders. Twitter and other popular forms may be unavailable in particular regions and others may not be top of mind to the intended message recipient.

This is **not** intended to be a messaging play. The messaging between wallets would likely be an extension or a more robust system. For the present market size, and needs, this can satisfy and grow into a more broad offering. Teams today need to find a way to message notify holders. Current option usually is something not far from an on-chain airdrop of spam.

### For recipients

Simplified, and extensible, this is for the most basic communication.

* Double opt-in between user and the token team (or broadcaster).
* Frequency of contact is defined by recipient.
* User could set a premium to jump over their spam filter?

An implementation like this provides an duel opt-in notification system (recipient and sender must agree on notifying them) which delivers transparency for all, and captures the awareness of the specific user.

To mitigate spam we ensure recipients must grant permission per broadcaster and the frequency in which they're willing to receive notifications. ABCtoken may deliver notifications to their holders every week summarizing their agenda. I may opt-in for notifications but specify a month as the minimum duration between these notifications. A monthly notification from ABCtoken. Others may opt- , just like they do with a trading venue  

### For senders


* Increase participation and curation of their network.
* Transparency in notifying all participants fairly.
* Broadcast to all, or deliver only to a select tier determined by balance held.

Keeping all things consistent, the one certainty is that they're a holder of a wallet that has already interacted with the token contract, unless airdropped without permission.

### Gas Usage

The current design accomodates for broadcasting a notification to an address. Be it a single address, or many. One of the points of feedback received was gas usage to broadcast the same notification to many. Event handling can help surface notifications, but still requires some mechanics for 1 to many.

As the ecosystem scales, there's likely more anonymity with DAO participants. Possible growth in value at risk for sharing a broadcast without permission, can still be supported in this lightweight design. For smaller broadcasts where gas is less of an issue all the way up to thousands of token holders needing to be notified.

Solutions could implement something similar to what we have with televisions I'd imagine. No expert, but this is a similar outcome to be achieved, so there's likely a lot that could be drawn from that. Some sort of leakage (tts?) identifier but not relevant for this in itself, would come on top of this I guess.

MakerDAO Message --> Uploaded to MakerDAO notification contract --> Event Triggered --> Wallets surface event

## Example functionality
Add a few functions ERC-20's interface:
```solidity
// Selective Notification Interface

contract selectiveNotification is ERC20 {

  // Lookup a specific holders permissions to the DAO notifying them. ?
function acceptable(address _owner, address _sender) constant returns (uint256 remaining)

  // Broadcaster - Send memo's and define who you want it to get to?
function notification(address _to, uint256 _group, string _note) returns (bool success)

  // Recipients - Recipient 
function accept(address _sender, uint256 _count, uint256 _interval) returns (bool success)

  // Notification - Wallets
  
  Event (notification --> Trigger to wallets like metamask etc... --> Wallet adds a notification if applicable to the wallet holder --> Wallet holder takes action.
```


### acceptable
```solidity
function acceptable(address _owner, address _sender) constant returns (uint256 remaining)
```
Returns the duration until ```_sender``` is allowed to notify ```_owner```.

### notification
```solidity
function notification(address _to, uint256 _group, string _note) returns (bool success)
```
The ```_note``` will then be accessible for ```_to```, who is the recipient. If contract is specified, all holders can receive? Added in ```_group``` which could pass through a specific demographic. E.g. You could have it passed in as duration of holdings, or as count of assets held. Targeting a certain tier of asset holders by how long, or by how much etc...

### accept
```solidity
function accept(address _sender, uint256 _count, uint256 _interval) returns (bool success)
```
Allow ```_sender``` to notify you, a certain amount of times, up to the ```_count``` amount. If this function is called again it overwrites the current values specified. Granting a sender permission to notify me a pre-determined amount, given that the ```_interval``` has been passed. Some services may need more frequent updates than others. Quarterly reporting vs weekly voting, etc... Rough example for MakerDAO.

## Thoughts appreciated!
This is not my area of expertise, but definitely keen for this to exist and hopefully this can help create a standard for teams to have this notification capacity. Really hindering the ecosystem at the moment and given that these things take time and iterations, better to start sooner than later :)

Thank you!

Kind regards,

Michael.

*Thanks for the feedback on things to clarify or consider. Appreciate it!
