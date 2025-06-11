## **👋 Welcome to Homio**

Homio is a clean, minimal, and fully YAML-based dashboard for Home Assistant that i build for a bit of fun. It's still work in progress but wanted to share it with you after receiving many requests for it. It’s built with tablets in mind — perfect for a wall-mounted screen — but it also works well on mobile thanks to its responsive layout.

Everything is done in YAML to give you full control and make it easier to share, reuse, and tweak. No UI editors here — just clean files and templates that you can version, back up, and build on.



## **✅ What You’ll Need**

Before jumping in, make sure you’ve got the basics covered:

1. Home Assistant in storage Mode
Even though Homio is written entirely in YAML, you should leave the Lovelace mode set to storage in configuration.yaml. This allows you to keep using the UI editor for other dashboards, while loading Homio as a YAML dashboard.

```text
lovelace:
  mode: storage
  dashboards:
    dashboard-homioy:
      mode: yaml
      title: "homio"
      icon: mdi:star-plus-outline
      show_in_sidebar: true
      filename: dashboards/homio/homio.yaml
```

3. A Few Custom Cards
Homio uses a couple of custom cards.

button-card by Romraider — https://github.com/custom-cards/button-card 

This is the main building block of Homio.

layout-card by Thomas Loven — https://github.com/thomasloven/lovelace-layout-card

You’ll need to use the slightly modified version included in this repo to support extra CSS properties.

This card need to be installed here

/www/community/layout-card-modified/layout-card-modified.js


## 📁 Folder Structure

Everything lives under `/config` in your Home Assistant setup:

```text
/config
│
├── dashboards/
│   └── homio/
│       └── homio.yaml               # Main dashboard YAML file
│
├── dashboards/templates/
│   ├── includes/                    # Layout includes and card groups
│   │   ├── layouts/                 # Layout-specific YAML includes
│   │   └── rooms/                   # Optional: room-specific cards
│   └── templates/                   # All button-card templates
│       └── homio_templates.yaml
│
├── helpers/
│   └── homio_helpers.yaml          # All required helpers (input_booleans, numbers, etc.)
│
├── themes/
│   └── homio/
│       └── homio.yaml              # The Homio theme
│
├── sensors.yaml                    # Any custom sensors used by Homio
│
├── automations.yaml
├── scripts.yaml
├── scenes.yaml
└── configuration.yaml              # Where includes are added
```

## **💡 What Goes Where?**

**homio.yaml:** Your main dashboard file. This is where each screen and layout is defined.

**homio_templates.yaml:** All your button-card templates live here — nice and tidy.

**includes/:** Used for reusable layout snippets and grouped cards, so the main dashboard stays clean.

**homio_helpers.yaml:** All required helpers (like input_booleans or input_numbers) go here. No need to create them through the UI.

**homio.yaml (theme):** The visual style of Homio. Works best with a minimal, soft look.

## **🖼️ Assets Setup – Images & Icons**

To make Homio look the way it’s intended, you’ll need to add your own room images and icons to the www folder in Home Assistant. These are used for things like room backgrounds and custom icons inside button cards. I dont use the built in mdi icons as i dont like them, i do use the material icons though but download them from google at the 100 weight as i feel they fitted my design better. I will include these in the repo and i plan to keep adding to them as well.

https://fonts.google.com/icons?icon.query=light

📁 Folder Structure
Inside your /config/www directory, create the following folders:

```
www/
└── images/
    └── Homio/
        ├── rooms/       ← Background images for rooms
        └── icons/       ← SVG icons used in entity cards

```

🖼️ Room Backgrounds
Place your .jpg files in:

```
/config/www/images/Homio/rooms/
```

Make sure the file names match what you use in the image: variable (without the file extension). For example:

```
image: living_room  # Will load living_room.jpg
```

🧩 Icons
Put your .svg icon files here:

```
/config/www/images/Homio/icons/
```

These are used for visual cues like heating, doors, or lights. You can reference them with:

```
entity_picture: /local/images/Homio/icons/heating.svg
```
