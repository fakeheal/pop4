---
title: "From yellowed to mint: reviving an original Game Boy"
date: 2024-01-20
issue: 1
layout: restoration
summary: "A yellowed, dead DMG-01 from a second-hand marketplace gets an IPS screen, a mint shell and new buttons."
why: "I found it pretty cheap on a second-hand marketplace. I'd never owned one and knew almost nothing about it, but I'd watched a few restoration videos and wanted to try one myself."
tags: [nintendo, soldering]
featured: true
draft: false
cover: "after.jpg"
factcheck: "Part names and prices are from my order receipt. I ordered in January 2024 and paid in BGN; prices are converted to EUR at the fixed rate of 1 EUR = 1.95583 BGN."

status: "done"
before: { src: "before.jpg", alt: "Original Game Boy with a yellowed shell and a dim green screen" }
after: { src: "after.jpg", alt: "Rebuilt Game Boy in a mint shell with a bright IPS screen showing Pokémon Trading Card Game" }
ba_style: slider     # slider (default) | split (side by side)

project:
  - { k: "Console", v: "Game Boy (DMG-01)" }
  - { k: "Screen", v: "Funnyplaying Retro Pixel IPS" }
  - { k: "Shell", v: "IPS-ready housing, light blue" }
  - { k: "Time", v: "3 hours, single evening" }
  - { k: "Difficulty", v: "●●●○○ needs soldering" }

currency: "€"
parts:
  - { item: "Retro Pixel IPS LCD kit", url: "https://www.zedlabz.com/en-eu/products/retro-pixel-ips-lcd-screen-for-nintendo-game-boy-dmg-01-console-funny-playing?variant=38153240150187", cost: 57.26 }   # 112.00 BGN
  - { item: "IPS-ready housing shell, light blue", url: "https://www.zedlabz.com/en-eu/products/modified-ips-screen-ready-housing-shell-for-nintendo-game-boy-dmg-01-console-light-blue-funnyplaying?variant=38198859333803", cost: 11.25 }   # 22.00 BGN
  - { item: "Screen centering bracket", url: "https://www.zedlabz.com/en-eu/products/bracket-for-nintendo-game-boy-dmg-01-retro-pixel-ips-lcd-screen-mod-clear-zedlabz?variant=38154031104171", cost: 5.62 }    # 11.00 BGN
  - { item: "Glass lens for Retro Pixel IPS, white", url: "https://www.zedlabz.com/en-eu/products/glass-lens-screen-for-nintendo-game-boy-dmg-01-retro-pixel-ips-lcd-screen-modded-console-white-zedlabz?variant=38153464545451", cost: 5.11 }    # 10.00 BGN
  - { item: "Button set A/B/D-pad/power, white", url: "https://www.zedlabz.com/en-eu/products/button-set-for-nintendo-game-boy-original-dmg-01-a-b-d-pad-power-switch-replacement-og-dmg-funnyplaying?variant=43072962429180", cost: 4.60 }    # 9.00 BGN
  - { item: "Screw set for DMG housing, 10 pack", url: "https://www.zedlabz.com/en-eu/products/full-compatible-screw-set-for-original-nintendo-game-boy-dmg-01-housing-replacement-10-pack-zedlabz?variant=31903450562662", cost: 3.07 }    # 6.00 BGN
  - { item: "Battery contacts set", url: "https://www.zedlabz.com/en-eu/products/zedlabz-battery-terminal-spring-contacts-set-contacts-kit-for-nintendo-game-boy-original-dmg-01?variant=29217629189", cost: 3.07 }    # 6.00 BGN
  - { item: "Tri-wing & Philips screwdriver set", url: "https://www.zedlabz.com/en-eu/products/tri-wing-philips-precision-screwdriver-set-for-various-handheld-consoles-funnyplaying?variant=43283970949372", cost: 5.11 }    # 10.00 BGN

tools: ["Tri-wing screwdriver", "Philips screwdriver", "Soldering iron", "solder", "flux", "tweezers"]

steps:
  - title: "Teardown"
    text: "Tri-wing screws out, back shell off, then the two boards separated. I photographed every connector before unplugging it."
    image: "before.jpg"
    done: true
  - title: "Installing the IPS kit"
    text: "The Retro Pixel screen goes into the IPS-ready shell with the centering bracket, so it sits straight behind the lens. The only soldering is the speaker (more on that below)."
    image: "retro-pixel-ips-lcd-screen.jpg"
    done: true
  - title: "New shell, contacts and buttons"
    text: "Everything goes into the mint housing: new battery contacts in the back, white A/B buttons and D-pad in the front."
    image: "after.jpg"
    done: true
---

## Starting condition

The grey shell had turned an uneven yellow, with a lighter patch below the logo where something had covered it from the sun. The screen was the usual green-on-green, hard to read, with a dark blotch in the lower left. The A and B buttons had faded to pink. The battery compartment was rusty and the console didn't turn on, which could have been any number of things.

I didn't want to just restore it, I wanted to upgrade it.

## The plan

I've seen videos of people fixing yellowed plastic with peroxide and UV lights, but buying that setup for one console didn't make sense. So I replaced almost everything instead:

- an IPS screen: backlit, sharp, and readable without a lamp next to you
- a shell that's already cut for that screen, so I didn't have to trim any plastic
- new battery contacts, buttons and screws

{{< callout "Why mint?" >}}
It's one of my favorite colors and it was in stock at ZedLabz. It also matches this blog's background.
{{< /callout >}}

## Steps

{{< steps >}}

## The soldering part

![Soldering the speaker wires to the new front board](soldering.png "Photo: RetroGameJoy. I forgot to take one :(")

Less than I expected. The Retro Pixel kit comes with its own front board, so there's nothing to desolder from the old screen. The only joints are the speaker's two wires, which move from the original board to the new one. Polarity doesn't matter, so it's a good first soldering job.

## How it plays now

The screen is bright enough to play in bed with the lights off, and I like how the white buttons and lens look on the mint shell. The first cartridge I tried was Pokémon Trading Card Game, which fits, since I'll be writing about card games in Play too.

## What I'd do differently

Near the end I got too excited and rushed to see the result. Even though I'd taken pictures at every step, I put one of the longer screws in the wrong hole, and it pushed through the front a little (that's the small white dot above Start/Select). I was a bit sad, but the console works fine. Maybe I'll cover it with a cute sticker that goes with the shell, IDK. Next time I'll sort the screws by length before closing it up.
