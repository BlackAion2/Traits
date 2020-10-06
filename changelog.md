# Carnalitas v1.2.3

## New Features

### Prostitution System

* You can now force your slaves to earn money for you as prostitutes (up to a maximum of 10 slave-prostitutes). This is a great way to earn money, but it will tank your piety really quickly if slavery or prostitution is shunned in your faith.

### Personality Replacement Library for Modders

Added a group of scripted effects that remove a random personality trait and replace it with a trait of your choice. This is meant for slave training/brainwashing effects but the possibilities are limitless.

* `carn_exclude_trait_from_personality_replacement_effect` (requires `TRAIT`)
* `carn_create_personality_replacement_effect` (requires `NEW_TRAIT`)
* `carn_resolve_personality_replacement_effect`
* `carn_clear_personality_replacement_effect`

You can use `carn_has_replaceable_personality_trait_trigger` to check whether a character has personality traits that are not flagged as "irreplaceable."

To mark a trait as irreplaceable for `carn_has_replaceable_personality_trait_trigger`, use `carn_set_personality_trait_as_irreplaceable_trigger` (requires `TRAIT`).

For example, here is an event that makes women lustful, content, or trusting:

```
sluttification.0001 = {
    type = character_event
    title = sluttification.0001.t
    
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
    
    theme = seduce_scheme
    left_portrait = {
        character = scope:recipient
        animation = flirtation_left
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

* Changed relationship and family panels slightly to better accomodate larger numbers of spouses, concubines/consorts and wards. Inspired by Better Character UI, but as usual our implementation is even better because it defaults to the normal UI and only changes if you need the extra space.
* Changed Trait panel to show a scroll area when a character has a large amount of traits.

New scripted triggers:
* `carn_relationship_allows_free_sex_trigger` (requires `PARTNER`)

## Tweaks

### Sex Scene System

* Requesting a noncon scene with the game rule "Dubious Consent Only" enabled will now request a dubcon scene instead of a consensual scene.

### Lay With Lover/Make Love

* Changed the name of this interaction to Make Love.
* Now allows you to pay to Make Love to prostitutes.
* Reduced the amount of Stress lost.
* Reduced the cooldown to 1 year.

### Stress from Arousal

* Now triggers every year, but grants a reduced amount of stress.

### Prostitution System

* Significantly increased the chance for random prostitution events to happen.
* The Sell Slave window now opens to the wealthiest character able to buy a slave from you.

## Bug Fixes

* Fixed requested sex scene flags not being cleared properly, causing the fallback event to sometimes not appear.
* Fixed prostitution random events being less affected by traits than intended.
* Fixed prostitutes only being able to rank up if they're ugly or dumb. They will now correctly rank up if they *aren't* ugly or dumb.
* Fixed errors being thrown due to attempting to seed traits on dead characters.
* Fixed sex between slave owners and slaves not correctly requesting noncon/dubcon scenes.
* Fixed `carn_increase_dick_size_one_step_effect` accidentally being overwritten and doing nothing.