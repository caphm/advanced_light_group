# Advanced Light Group

## What this does
This is an extension of the built-in Light Group integration in Home Assistant that allows for more fine grained control of the lights in a light group.
It distinguishes between main and auxiliary lights:
- When turning the light group on, only main lights will be turned on
- When turning the light group off, all lights (both main and auxiliary) will be turned off

This is useful if you have accent lighting that you don't want to turn on every time you enter a room, but want to be turned off along with all the other lights when leaving a room.

Also, when changing brightness, color, etc. while only a subset of the lights in the group are on, the change will only affect the already turned on lights. Lights that are off, will not be turned on.
This is useful if you have all lights excpt one turned off, e.g. for watching TV, and want to adjust brightness without the need to specify the exact name of the light.

## Setup

Add this to your `configuration.yaml`:
```
light:
  - platform: advanced_light_group
    name: Living Room Lights
    main_lights:
      - light.living_room_ceiling_light
      - light.living_room_spots
    aux_lights:
      - light.living_room_cabinet
      - light.christmas_tree
```

Entities that do not exist, are ignored. Thus you don't have to change your config when you remove your christmas tree lights after the season for example.

## Configuration options

Key | Type | Required | Default | Description
-- | -- | -- | -- | --
`name` | `string` | `False` | `Advanced Light Group` | The name of the resulting light entity
`main_lights` | `list` | `True` |  | Which lights are considered main lights
`auxiliary_lights` | `list` | `False` |  | Which lights are considered auxiliary lights
