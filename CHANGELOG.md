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

### Fetish System ###

Fetish system has been reworked again.

* Fetish flags are no longer prefixed with `carn_fetish_`. So for example, the fetish that was formerly `carn_fetish_anal` is now `anal`.
* All fetish-specific scripted effects are deprecated. Use `carn_add_fetish_effect` instead.
* Added custom GUI to the character window showing a character's fetishes. Due to engine limitations, only hardcoded fetishes are supported.

New fetishes:
* `raping`
* `being_raped`
* `lactation`

New scripted effects:
* `carn_give_deviant_secret_or_trait_no_fetish_effect`
* `carn_give_deviant_secret_or_trait_if_has_any_fetish_effect`
* `carn_remove_deviant_secret_or_trait_if_has_no_fetishes_effect`

New on_actions:
* `carn_on_new_random_fetish` - add new fetishes to this on_action
* `carn_on_gain_fetish`
* `carn_on_lose_fetish`

Renamed scripted effects:
* `carn_add_given_fetish_effect` to `carn_add_fetish_effect`
* `carn_remove_given_fetish_effect` to `carn_remove_fetish_effect`

Renamed scripted triggers:
* `carn_has_given_fetish_trigger` to `carn_has_fetish_trigger`

Steps to add a new fetish:
* Decide on a tag. Here we will use `EXAMPLE`
* Add a fetish gaining event to `carn_on_add_random_fetish`
* Create effect localization for `carn_add_fetish_EXAMPLE_effect`
* Create scripted GUI for `carn_fetish_gui_EXAMPLE`
* Add your effect to the fetish icon in `character_window.gui`

### (Modding) Exclude Sex Scene Flags

Added the ability to exclude specific flags when requesting a sex scene.

New scripted effects:
* `carn_sex_scene_exclude_giving_player`
* `carn_sex_scene_exclude_receiving_player`
* `carn_sex_scene_exclude_dom_player`
* `carn_sex_scene_exclude_sub_player`
* `carn_sex_scene_exclude_oral`
* `carn_sex_scene_exclude_vaginal`
* `carn_sex_scene_exclude_anal`
* `carn_sex_scene_exclude_handjob`
* `carn_sex_scene_exclude_masturbation`
* `carn_sex_scene_exclude_orgy`
* `carn_sex_scene_exclude_cum_inside`
* `carn_sex_scene_exclude_cum_outside`
* `carn_sex_scene_exclude_consensual`
* `carn_sex_scene_exclude_noncon`
* `carn_sex_scene_exclude_dubcon`
* `carn_sex_scene_exclude_painful`
* `carn_sex_scene_exclude_bdsm`
* `carn_sex_scene_exclude_bestiality`
* `carn_sex_scene_exclude_petplay`
* `carn_sex_scene_exclude_bondage`
* `carn_sex_scene_exclude_toy`
* `carn_sex_scene_exclude_watersports`
* `carn_sex_scene_exclude_scat`
* `carn_sex_scene_exclude_gore`

### (Modding) Pregnancy Suppression

This new group of character and trait flags allows modders to suppress various events that trigger from `on_pregnancy` on_actions.

This allows you to do events like Adroit Religion's sacred orgy where a child that would normally be considered a bastard has a different pregnancy event instead.

Use the new on_actions, `carn_on_pregnancy_maintenance_suppressed` and `carn_on_pregnancy_notification_suppressed`, to add your own pregnancy events in place of the suppressed events. You can use a unique character flag to differentiate your suppressed pregnancy from the suppressed pregnancies of other mods.

Note that your new pregnancy notification event will have to do all the groundwork of adding the `pregnant` trait, playing music cues, etc.

New trait and character flags:
* `carn_suppress_all_on_pregnancy_maintenance`
* `carn_suppress_all_on_pregnancy_notification`

New character flags (not trait flags):
* `carn_suppress_next_on_pregnancy_maintenance`
* `carn_suppress_next_on_pregnancy_notification`

New on_actions:
* `carn_on_pregnancy_maintenance_suppressed`
* `carn_on_pregnancy_notification_suppressed`

New scripted triggers:
* `carn_should_suppress_on_pregnancy_maintenance_trigger`
* `carn_should_suppress_on_pregnancy_notification_trigger`

### (Modding) Absolute Birth Control

The `carn_absolute_birth_control` trait flag or character flag will completely block a character from ever getting the Pregnant trait. It does this by replacing all vanilla on_pregnancy events with a hidden event that ends the pregnancy.

This is useful for situations where you want all of a character's pregnancies to be replaced with something else. It's also useful where you want to control a character's fertility, but don't want their infertility to affect marriage proposals, display in the UI, etc.

Note that the character can still be invisibly impregnated, and will return `is_pregnant = true` until the pregnancy is ended through script.

New character and trait flags:
* `carn_absolute_birth_control`

New scripted triggers:
* `carn_has_absolute_birth_control_trigger`
* `carn_has_normal_pregnancy_no_absolute_birth_control_trigger`

New on_actions:
* `carn_on_absolute_birth_control_end_pregnancy`

### (Modding) Custom Pregnancy System

Carnalitas now includes a system for modders to define custom pregnancies that will be recognized by all Carnalitas submods as a form of pregnancy, but are decoupled from the base game pregnancy system. This allows you to do interesting things like multi-stage pregnancies or pregnancies that result in something other than children.

Custom pregnancies are defined as two variables:
* `var:carn_custom_pregnancy`, which defines the type of pregnancy,
* `var:carn_custom_pregnancy_stage`, which defines the pregnancy stage.

You can start a custom pregnancy with `carn_start_custom_pregnancy_effect`. This initializes `var:carn_custom_pregnancy` as an arbitrary string, and `var:carn_custom_pregnancy_stage` as 0.

As part of `carn_start_custom_pregnancy_effect` you also have to define a number of days. After that many days, the stage will increase by 1 and the on_action `carn_on_custom_pregnancy_stage_change` will fire.

By hooking into `carn_on_custom_pregnancy_stage_change` with your own events, and using `carn_setup_delayed_custom_pregnancy_stage_change` to trigger additional stage changes after a certain amount of time, you can theoretically have as many stages of pregnancy as you want.

On the final stage, you can have an event where the pregnancy comes to term. Fire any effects, remove any traits you added, and use `carn_end_custom_pregnancy_effect` to clean up variables.

While you could theoretically replicate all of these effects on your own, the real power of this system is in integrating all different kinds of custom pregnancies with a unified set of triggers. This way, if your mod makes a character pregnant with eggs, and another mod wants to make the same character pregnant with a demonspawn, they won't step on each others' toes.

New scripted effects:
* `carn_start_custom_pregnancy_effect` (requires `PREGNANCY_TYPE`, `DAYS_UNTIL_NEXT_STAGE`, `CAN_BE_ABORTED`)
* `carn_setup_delayed_custom_pregnancy_stage_change` (requires `DAYS`)
* `carn_end_custom_pregnancy_effect`

New scripted triggers:
* `carn_is_pregnant_trigger`
* `carn_is_visibly_pregnant_trigger`
* `carn_has_any_custom_pregnancy_trigger`
* `carn_has_custom_pregnancy_type_trigger` (requires `PREGNANCY_TYPE`)
* `carn_custom_pregnancy_stage_equals_trigger` (requires `STAGE`)
* `carn_custom_pregnancy_can_be_aborted_trigger`

New character flag (not trait flags):
* `carn_block_aborting_next_custom_pregnancy` (prevents custom pregnancy from being overwritten)

New trait flags:
* `carn_custom_pregnancy` (put on your equivalent of the Pregnant trait for scripts)
* `carn_use_pregnant_portrait` (shows a pregnant belly on the character)

New on_actions:
* `carn_on_custom_pregnancy_stage_change`
* `carn_on_start_custom_pregnancy`
* `carn_on_end_custom_pregnancy`
* `carn_on_custom_pregnancy_replace_normal_pregnancy`
* `carn_on_custom_pregnancy_failed_to_replace_normal_pregnancy`
* `carn_on_custom_pregnancy_replace_custom_pregnancy`
* `carn_on_custom_pregnancy_failed_to_replace_custom_pregnancy`

### Abortion Library

These triggers are meant for mods dealing with abortion.

New scripted triggers:
* `carn_normal_or_custom_pregnancy_can_be_aborted_trigger`
* `carn_normal_pregnancy_can_be_aborted_trigger`

New trait and character flags:
* `carn_block_aborting_any_pregnancy`
* `carn_block_aborting_any_normal_pregnancy`
* `carn_block_aborting_any_custom_pregnancy`

New character flags (not trait flags):
* `carn_block_aborting_next_normal_pregnancy` (removed after pregnancy ends)
* `carn_block_aborting_next_custom_pregnancy` (removed after pregnancy ends)

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
* Fixed `carn_has_any_fetish_trigger` not working properly.