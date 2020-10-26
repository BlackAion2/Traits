# Carnalitas v1.3

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

When the system is active, women will start lactating when they gain the Pregnant trait. Their milk production is initially low, but they can increase it by having many children in short succession. If a woman is not pregnant her milk production will taper off and eventually stop.

The system is fairly bare bones, but it offers a framework for mods to induce lactation, increase milk productivity, have events that tie into a character's milk production level, and so on.

New scripted effects:
* `carn_set_milk_production_effect` (requires `VALUE`)
* `carn_stop_milk_production_effect`
* `carn_change_milk_production_effect` (requires `VALUE`)
* `carn_change_milk_production_with_maximum_effect` (requires `VALUE`, `MAXIMUM`)
* `carn_set_milk_production_minimum_effect` (requires `MINIMUM`)
* `carn_set_milk_production_maximum_effect` (requires `MAXIMUM`)

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

* Custom localization will now correctly give "a hermaphrodite" not "an hermaphrodite."
* Being a futa will no longer block you from the Strengthen Bloodline decision.
* Bedchamber event background now actually uses the bedchamber illustration that was included with the game.
* The Make Love notification will now prioritize any spouse or concubine that you are attracted to.
* You can no longer Make Love to prostitutes who aren't currently working.
* Make Love interaction will no longer appear in the menu if either participant is a child.
* If you turn a slave into a prostitute, they will now hate you unless they have a submission fetish.
* Fixed positive prostitution events becoming less common if you're a good prostitute, rather than more common.
* Modding: Renamed the IDs of many game rules to be more internally consistent.