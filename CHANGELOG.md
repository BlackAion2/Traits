# Carnalitas v1.2.4

## New Features

### Fetish System
Fetish system has been reworked to only give a fetish to characters with a `deviant` trait/secret.

New triggers:
* `carn_has_a_fetish_trigger`
* `carn_has_given_fetish_trigger` (requires `FETISH`)

New effects to add fetishes:
* `carn_add_random_fetish_effect`
* `carn_add_fetish_anal_effect`
* `carn_add_fetish_sadism_effect`
* `carn_add_fetish_masochism_effect`
* `carn_add_fetish_bestiality_effect`
* `carn_add_fetish_watersports_effect`
* `carn_add_fetish_scat_effect`
* `carn_add_fetish_gore_effect`
* `carn_add_fetish_foot_play_effect`
* `carn_add_fetish_bondage_effect`
* `carn_add_fetish_domination_effect`
* `carn_add_fetish_submission_effect`
* `carn_add_given_fetish_effect` (requires `FETISH`)

When using `carn_add_given_fetish_effect` the given `FETISH` is not required to be in the list above. This is so mods can use their own custom fetishes.

New effects to remove fetish:
* `carn_remove_all_fetishes_effect`
* `carn_remove_given_fetish_effect` (requires `FETISH`)

List of fetishes (`flag:` not necessary anymore):
* `carn_fetish_anal`
* `carn_fetish_sadism`
* `carn_fetish_masochism`
* `carn_fetish_bestiality`
* `carn_fetish_watersports`
* `carn_fetish_scat`
* `carn_fetish_gore`
* `carn_fetish_foot_play`
* `carn_fetish_bondage`
* `carn_fetish_domination`
* `carn_fetish_submission`

### Miscellaneous

* Added the scripted effects `carn_make_root_and_sex_partner_naked_for_this_event_effect` and `carn_make_root_and_sex_partner_no_longer_naked_effect`
* Added `can_not_be_granted_titles` as a character flag.
* added `carn_cannot_use_birth_control` as a trait and character flag.

## Bug Fixes

* Immortal characters will now be treated by Carnalitas as their effective age instead of their chronological age, allowing them to remain prostitutes, fetch higher prices as slaves, etc.
* Fixed an error in the "can no longer work as a prostitute" tooltip.
* Fixed the variable list `carn_personality_replacement_excluded_traits` persisting forever, screwing up future personality replacement effects of a different type.