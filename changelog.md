# Carnalitas v1.2.2

## New Features

### Miscellaneous

* Now integrates Show More Traits from Steam Workshop, so you no longer need to use that mod. Our implementation is actually even better than the Workshop version because the super-small grid only appears if needed.
* Changed relationship and family panels slightly to better accomodate larger numbers of spouses, concubines/consorts and wards. Inspired by Better Charqacter UI.

## Tweaks

### Slavery System

* Slave relations GUI now uses amazing scrollbar technology, allowing you to see 7 rivals AND 7 slaves without needing to expand either box.
* Slaves will now be automatically freed if they somehow get any title.
* You can now see how much a slave will sell for in the Sell Slave tooltip.
* You can now sell slaves to people who can't afford a slave's full price. You will just get whatever they can pay. (The AI on the other hand won't be so generous and will always ask for the full price when selling you a slave.)
* Clarified the factors that affect a slave's price in the Slave Market encyclopedia entry/tooltip.

New on_actions for modders:
* `carn_on_slave_enslaved`
* `carn_on_slave_freed`

## Bug Fixes

### Slavery System

* Fixed children born from slaves having no owner.
