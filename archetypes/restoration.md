---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
{{- $max := 0 }}{{ range site.RegularPages }}{{ with .Params.issue }}{{ if gt (int .) $max }}{{ $max = int . }}{{ end }}{{ end }}{{ end }}
# NEXT ISSUE NUMBER: the highest issue found when this file was created was #{{ printf "%03d" $max }}.
# Check that nothing else claimed #{{ printf "%03d" (add $max 1) }} in the meantime, then keep or change it.
issue: {{ add $max 1 }}
summary: ""          # subtitle under the title and the text on cards
why: ""              # "Why this project" callout
tags: []             # free tags, lowercase: marvel, nintendo, star-wars, fantasy, sci-fi…
featured: false      # true = candidate for the homepage featured slot (newest featured wins)
factcheck: ""        # optional "Fact-check note" callout at the end
cover: ""            # used for the homepage featured slot; falls back to `after`
draft: true
layout: restoration
status: "in-progress"   # in-progress | on-hold | done ("step X of Y" = steps marked done)
before: ""           # "before.jpg" or { src: "before.jpg", alt: "yellowed shell" }
after: ""
project:             # "Project card" box
  - { k: "Console", v: "" }
  - { k: "Started", v: "{{ now.Format "Jan 2, 2006" }}" }
parts:               # total is summed automatically
  - { item: "", url: "", cost: 0.00 }   # url is optional: links the part name
currency: "€"
tools: []
steps:               # done: false renders faded; image: "step1.jpg" or { src, alt }
  - { title: "", text: "", image: "", done: false }
---

## Starting condition

## Steps

{{</* steps */>}}

## What I'd do differently
