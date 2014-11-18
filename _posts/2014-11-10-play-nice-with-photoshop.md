---
layout: post
title: Play Nice With Photoshop
description: "These are a list of common practices we've gathered for delivering design materials to improve the clarity of a PSD's when transferred from design to production."
category: Design
tags: [Docs, Design, Photoshop, Workflow, Tips]
comments: true
share: true
---
These are a list of common practices we've gathered for delivering design materials to improve the clarity of a PSD's when transferred from design to production.


## External file organisation
- **Consolidate your PSD files.** Only use a minimal number of PSDs.
- **Name files appropriately.** 
For example: "ClientName_desktop.psd", "ClientName_tablet.psd" and "ClientName_mobile.psd". 
Not: "newest.psd", "LATEST.psd" or "Final_v2.psd".
- **Store all assets relative to PSD.** Keep stock-photos/icons/fonts  in a folder close to the PSD, preferably in a folder labeled "assets".
- **Make a separate template for all global UI elements.** Making a PSD strictly for user interface treatments (buttons, forms, etc.) with all different states (:hover, :active, errors) helps during the development phase.
- **Make a separate template or style guide for setting typography (font families, sizes, colours, etc.).** This helps making sure that the typography stays consisted throughout the project.


## Internal file organisation
- **Name layers appropriately.**
- **Organise layers in folders.**
- **Delete unnecessary layers.**
- **Use layer comps and smart objects.**


## Setting typography
- **Set font size in pixels, not points.**
- **Use whole pixel values.** Refrain from resizing text with the Free Transform tool and give it a whole number value instead.
- **Set type colour with colour picker, not using opacity or fill.**
- **Don't rasterize or flatten type.**


## Image elements
- **Keep logos, icons, buttons and other graphical elements as vector smart objects.** This is required for creating assets for high pixel ratio displays (Retina displays) or if resizing is needed.
