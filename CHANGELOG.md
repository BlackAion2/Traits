# Carnalitas 1.3.2

Compatible with saved games from version 1.3 and up.

## New Features

### Fetishes

* Gave all fetishes a corresponding game concept description.

### (Modding) Pregnancy Suppression System

* Added a birth notification suppression system that functions similarly to pregnancy suppression. This allows you to replace `birth.1001` and similar events with your own event in `carn_on_birth_notification_suppressed`. Note that you will need to replace both mother and father notification events.

New character and trait flag:

* `carn_suppress_all_on_birth_notification`

New character flag (not trait flag):

* `carn_suppress_next_on_birth_notification`

New on_action:

* `carn_on_birth_notification_suppressed`

## Tweaks

* Fetish GUI is no longer hardcoded from the character window. Instead it is now reliant on a list in scripted_gui which should be easier to maintain.

## Bug Fixes

* Fixed pregnancy events having multiple sets of options. This fix overrides `pregnancy_events.txt`
* Randomly generated peasant/populist rebellion leaders which are made into slaves no longer disappear if captured in battle.