# Carnalitas v1.2.3

## New Features

### Personality Replacement Library for Modders

Added a group of scripted effects that remove a random personality trait and replace it with a trait of your choice. This is meant for slave training/brainwashing effects but the possibilities are limitless.

* `carn_exclude_trait_from_personality_replacement_effect` (requires `TRAIT`)
* `carn_create_personality_replacement_effect` (requires `NEW_TRAIT`)
* `carn_resolve_personality_replacement_effect`
* `carn_clear_personality_replacement_effect`

You can use `carn_has_replaceable_personality_trait_trigger` to check whether a character has personality traits that are not flagged as "irreplaceable." To set a trait as irreplaceable use `carn_set_personality_trait_as_irreplaceable_trigger` (requires `TRAIT`).

For example, here is an event that makes women lustful, content, or trusting:

```
sluttification.0001 = {
    type = character_event
    title = sluttification.0001.t

	theme = seduce_scheme
	left_portrait = {
		character = scope:recipient
		animation = flirtation_left
	}

    desc = {
		desc = sluttification.0001.desc.opening
        triggered_desc = {
            trigger = {
                scope:carn_new_trait = flag:lustful
            }
            desc = sluttification.0001.desc.gained_lustful
        }
        triggered_desc = {
            trigger = {
                scope:carn_new_trait = flag:content
            }
            desc = sluttification.0001.desc.gained_content
        }
        triggered_desc = {
            trigger = {
                scope:carn_new_trait = flag:trusting
            }
            desc = sluttification.0001.desc.gained_trusting
        }
    }

    trigger = {
        scope:recipient = {
            is_female = yes
            carn_can_have_sex_trigger = yes

            # This checks that the character has a trait that is not lustful, content, or trusting
            carn_set_personality_trait_as_irreplaceable_trigger = { TRAIT = lustful }
            carn_set_personality_trait_as_irreplaceable_trigger = { TRAIT = content }
            carn_set_personality_trait_as_irreplaceable_trigger = { TRAIT = trusting }
            carn_has_replaceable_personality_trait_trigger = yes
        }
    }

    immediate = {
        scope:recipient = {
            carn_exclude_trait_from_personality_replacement_effect = { TRAIT = lustful }
            carn_exclude_trait_from_personality_replacement_effect = { TRAIT = content }
            carn_exclude_trait_from_personality_replacement_effect = { TRAIT = trusting }
            random_list = {
                10 = {
                    trigger = {
                        NOT = { has_trait = lustful }
                    }
                    carn_create_personality_replacement_effect = { NEW_TRAIT = lustful }
                }
                10 = {
                    trigger = {
                        NOT = { has_trait = content }
                    }
                    carn_create_personality_replacement_effect = { NEW_TRAIT = content }
                }
                10 = {
                    trigger = {
                        NOT = { has_trait = trusting }
                    }
                    carn_create_personality_replacement_effect = { NEW_TRAIT = trusting }
                }
            }
        }
    }

    option = { # Encourage the personality change
        name = sluttification.0001.a
        scope:recipient = {
            carn_resolve_personality_replacement_effect = yes
            # This will show the tooltip for losing and gaining traits correctly.
        }
    }

    option = { # Tell her to remain as she is
        name = sluttification.0001.b
    }
}
```

### Miscellaneous

* Changed relationship and family panels slightly to better accomodate larger numbers of spouses, concubines/consorts and wards. Inspired by Better Character UI.

## Tweaks

### Prostitution System
* Significantly increased the chance for random prostitution events to happen.

## Bug Fixes

* Fixed prostitutes only being able to rank up if they're ugly or dumb. They will now correctly rank up if they *aren't* ugly or dumb.
* Fixed errors being thrown due to attempting to seed traits on dead characters.