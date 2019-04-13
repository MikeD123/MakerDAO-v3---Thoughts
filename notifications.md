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


## Example functionality
Add two functions ERC-20's interface, adding two functions:
```solidity
// Selective Notification Interface

contract selectiveNotification is ERC20 {

  // Lookup a specific holders permissions to the DAO notifying them. ?
function acceptable(address _owner, address _sender) constant returns (uint256 remaining)

  // Broadcaster - Send memo's and define who you want it to get to?
function notification(address _to, string _note) returns (bool success)

  // Recipients - Recipient 
function accept(address _sender, uint256 _count, uint256 _interval) returns (bool success)
```


###
```solidity
function acceptable(address _owner, address _sender) constant returns (uint256 remaining)
```
### notification
```solidity
function notification(address _to, string _note) returns (bool success)
```
The ```_note``` will then be accessible for ```_to```, who is the recipient. If contract is specified, all holders can receive?

### accept
```solidity
function accept(address _sender, uint256 _count, uint256 _interval) returns (bool success)
```
Allow _sender to notify you, a certain amount of times, up to the _count amount. If this function is called again it overwrites the current values specified. Granting a sender permission to notify me a pre-determined amount, given that the ```_interval``` has been passed. Some services may need more frequent updates than others. Quarterly reporting vs weekly voting, etc...  

### acceptable
```solidity
function acceptable(address _owner, address _sender) constant returns (uint256 remaining)
```
Returns the duration until ```_sender``` is still allowed to notify ```_owner```.

## Thoughts appreciated!