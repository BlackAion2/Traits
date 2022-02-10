# Carnalitas 1.6.1

Bugfix and quality of life release.

Compatible with saved games from Carnalitas 1.6 and up.

# Features

* Removed same-sex concubine interactions and scripts since they are in base game now.
* Guests who have desirable body part traits should now be correctly described in the court window.
** The description will be grammatically incorrect if you use Default trait names instead of Immersive ("A Big Tits woman"). This would take a ridiculous amount of effort to fix so you'll just have to deal with it.

# Bug Fixes

* Fixed cutoff age trigger text not showing properly. Again.

# Tweaks

* If you have the Divine Retribution perk, rape no longer incurs a piety loss and your court chaplain no longer gets a poor opinion of you. (It's still despicable though. You monster.)

# Modding

* You can now block Make Love with `carn_block_sex_interaction_to_opinion` and `carn_block_sex_interaction_from_opinion`

New scripted triggers:
* `carn_has_sex_blocking_disease_trigger`

New character and trait flags:
* `carn_block_send_sex_interaction`
* `carn_block_receive_sex_interaction`