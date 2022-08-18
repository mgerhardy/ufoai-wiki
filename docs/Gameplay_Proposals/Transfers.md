This is a proposal for the transfer model in UFO:AI. It covers
base-to-base transfers of goods and personnel, as well as buying/selling
things from and to the market, as well as personnel recruitment.

## The transfer model

The transfer model proposed here closely resembles the one seen in UFO:
Enemy Unknown. A "transfer" refers to a movement of a package materials
or personnel (or both), which is sent from one place to another. A
transfer takes time to complete, and until the transfer is completed the
contents are available to neither the source nor the destination.

A transfer should only be initiated once the player has finished
assembling the transfer package and has confirmed that he wishes the
transfer to be made and agrees to pay the price for the transfer.

Each transfer involves a cost, which is paid as soon as the transfer is
ordered. This cost consists of three parts:

- A fixed cost (equal for each and every transfer)
- A variable cost (determined by the contents and distance of the
  transfer)
- The cost of purchased goods and hired personnel (Only when buying,
  selling or hiring. When selling, this cost is negative)

Below is a breakdown of the various transfer types

### Base-to-base

In base-to-base transfers, the player pays the fixed and variable costs
for the transfer. The variable cost is fairly low for materials, but is
higher for personnel and live aliens.

### UFO Yard-to-UFO Yard

Similar to base-to-base transfers, except in the context of moving
captured UFOs between UFO yards.

### Buying/selling

When buying (and hiring), one end of the transfer process is unknown. In
this case, it is assumed that the transfer is made from an imaginary
base to the base where the purchase was made. The distance from this
imaginary base is always the same in all bases (i.e. there no real
on-map location for the origin of the transfer). The transfers from the
market should be trackable just like any other transfer, however.

When selling, there is a transfer from the base to the market, but no
costs are paid for this transfer. The player will get the full amount of
the sold items without added shipping and handling cost. It is assumed
the buyer pays for this. The transfer should still be timed, because the
items should not appear on the market instantly after the player has
sold them.

### Hiring/firing

When a player hires one or more new employees, a transfer is created
just like with purchasing materials. The fixed and variable costs will
be added to the hire price in the confirmation dialog.

When firing, there is no transfer. There are also no costs associated
with firing personnel. It is assumed the employees pay for their own
fare home. Fired employees are not re-added to the employee pool.

[Category:Proposals](Category:Proposals "wikilink")