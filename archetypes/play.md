---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
{{- $max := 0 }}{{ range site.RegularPages }}{{ with .Params.issue }}{{ if gt (int .) $max }}{{ $max = int . }}{{ end }}{{ end }}{{ end }}
# NEXT ISSUE NUMBER: the highest issue found when this file was created was #{{ printf "%03d" $max }}.
# Check that nothing else claimed #{{ printf "%03d" (add $max 1) }} in the meantime, then keep or change it.
issue: {{ add $max 1 }}
summary: ""          # subtitle under the title and the text on cards
why: ""              # "Why this deck" callout ("Why this main" for video game posts)
tags: []             # free tags, lowercase: marvel, nintendo, star-wars, fantasy, sci-fi…
featured: false      # true = candidate for the homepage featured slot (newest featured wins)
factcheck: ""        # optional "Fact-check note" callout at the end
cover: ""
draft: true
games: ""            # taxonomy: "Marvel Champions", "Pokémon TCG", "Star Wars Unlimited", "Marvel Rivals"…
hero: ""             # "Spider-Man · Justice" (hero · aspect)
hero_label: ""       # optional, default "Hero / aspect" ("Main" for video games)
record: ""           # "2W · 1L"
pool_as_of: ""       # "Nov 2026" or a patch name
pool_label: ""       # optional, default "Card pool as of" ("Patch" for video games)
sessions:            # result: win | loss | draw
  - { date: "", title: "", note: "", result: "win" }
deck:                # omit for video game posts
  - group: "Allies"
    cards:
      - { name: "", qty: 1 }
curve: {}            # optional cost curve, e.g. { "0": 3, "1": 8, "2": 10, "3": 5, "4+": 2 }
verdict: "tweak"     # retire | tweak | keep
# main:              # video game "main diary": shown in the sidebar instead of a decklist
#   hero: ""
#   role: ""
#   hours: ""
#   clicked: ""
---

## The plan

## Session log

{{</* sessions */>}}

## What's working

## What's getting cut
