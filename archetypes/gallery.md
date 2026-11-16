---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
{{- $max := 0 }}{{ range site.RegularPages }}{{ with .Params.issue }}{{ if gt (int .) $max }}{{ $max = int . }}{{ end }}{{ end }}{{ end }}
# NEXT ISSUE NUMBER: the highest issue found when this file was created was #{{ printf "%03d" $max }}.
# Check that nothing else claimed #{{ printf "%03d" (add $max 1) }} in the meantime, then keep or change it.
issue: {{ add $max 1 }}
summary: ""          # subtitle under the title and the text on cards
why: ""              # "Why this mini" callout
tags: []             # free tags, lowercase: marvel, nintendo, star-wars, fantasy, sci-fi…
featured: false      # true = candidate for the homepage featured slot (newest featured wins)
factcheck: ""        # optional "Fact-check note" callout at the end
cover: ""            # card image; falls back to photos.main
draft: true
layout: gallery
status: "in-progress"   # in-progress | on-hold | done
photos:              # the three hero images: "file.jpg" or { src: "file.jpg", alt: "…" }
  main: ""
  back: ""
  detail: ""
wip:
  - { image: "", caption: "Primed" }
recipe:
  - area: ""
    paints:
      - { name: "", hex: "#000000", role: "base" }
specs:
  - { k: "Scale", v: "" }
  - { k: "Time", v: "" }
  - { k: "Brushes", v: "" }
skills: []
---

## How it went

## Next time
