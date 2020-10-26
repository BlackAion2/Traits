# Carnalitas v1.3

**This update breaks save game compatibility, make sure to finish any games in progress first**

## New Features

### Rape System

* Added a character interaction to rape a prisoner in your dungeon. This is only available if you have both Make Love and noncon scenes enabled.
* Added a generic noncon dom scene and a generic noncon sub scene.

New scripted effects:
* `carn_rape_effect` (requires `RAPIST`, `VICTIM`, `TRIGGER_SEX_SCENE`)
* `carn_rape_opinion_effects_effect`
* `carn_rape_victim_stress_effect`

New scripted triggers:
* `carn_can_be_raped_trigger`

New character and trait flags:
* `carn_cannot_be_raped`

### Lactation System

Carnalitas now has a system to simulate character lactation. This is disabled by default but there are game rules to activate it for women, men, or all characters.

When the system is active, all characters have a milk production value, and women will gain milk production (and start lactating) when they get pregnant. When not pregnant a character's milk production will slowly decrease until they stop lactating.

The system is fairly bare bones, but it offers a framework for mods to induce lactation, increase milk productivity, have events that tie into a character's milk production level, and so on.

New scripted effects:
* `carn_create_milk_production_change_effect`
* `carn_resolve_milk_production_change_effect`
* `carn_set_milk_production_effect` (requires `VALUE`)
* `carn_stop_milk_production_effect`
* `carn_change_milk_production_effect` (requires `VALUE`)
* `carn_set_milk_production_minimum_effect` (requires `MINIMUM`)
* `carn_set_milk_production_maximum_effect` (requires `MAXIMUM`)
* `carn_send_milk_production_change_notification_effect`

See documentation for how to use these scripted effects.

New scripted triggers:
* `carn_can_lactate_trigger`
* `carn_is_lactating_trigger`
* `carn_milk_production_decreases_yearly_trigger`
* `carn_has_very_low_milk_production_trigger`
* `carn_has_low_milk_production_trigger`
* `carn_has_average_milk_production_trigger`
* `carn_has_high_milk_production_trigger`
* `carn_has_very_high_milk_production_trigger`
* `carn_has_extreme_milk_production_trigger`

New on_actions:
* `carn_on_start_lactating`
* `carn_on_stop_lactating`
* `carn_on_milk_production_change`

New character and trait flags:
* `carn_block_yearly_milk_production_decrease` (prevents lactation level from decreasing, like the Pregnant trait)

### Custom Pregnancy System

Added the trait flag `carn_pregnancy` for modders, meant for marking a trait as a kind of pregnancy (e.g. tentacle pregnancies from TD or dragon pregnancies from LF:DWSE). This will be expanded on in future updates.

New scripted trigger:
* `carn_is_visibly_pregnant_trigger`

### Miscellaneous

New scripted effects:
* `carn_undress_character_effect`
* `carn_dress_character_effect`

## Tweaks

* Being a futa will no longer block you from the Strengthen Bloodline decision.
* Bedchamber event background now actually uses the bedchamber illustration that was included with the game.
* The Make Love notification will now prioritize any spouse or concubine that you are attracted to.
* If you turn a slave into a prostitute, they will now hate you unless they have a submission fetish.
* Modding: Renamed the IDs of many game rules to be more internally consistent.

## Bug Fixes

* Custom localization will now correctly give "a hermaphrodite" not "an hermaphrodite."
* You can no longer Make Love to prostitutes who aren't currently working.
* Make Love interaction will no longer appear in the menu if either participant is a child.
* Fixed positive prostitution events becoming less common if you're a good prostitute, rather than more common.