---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
{{- $max := 0 }}{{ range site.RegularPages }}{{ with .Params.issue }}{{ if gt (int .) $max }}{{ $max = int . }}{{ end }}{{ end }}{{ end }}
# NEXT ISSUE NUMBER: the highest issue found when this file was created was #{{ printf "%03d" $max }}.
# Check that nothing else claimed #{{ printf "%03d" (add $max 1) }} in the meantime, then keep or change it.
issue: {{ add $max 1 }}
summary: ""          # subtitle under the title and the text on cards
why: ""              # "Why I picked it up" callout
tags: []             # free tags, lowercase: marvel, nintendo, star-wars, fantasy, sci-fi…
featured: false      # true = candidate for the homepage featured slot (newest featured wins)
factcheck: ""        # optional "Fact-check note" callout at the end
cover: ""            # image in this folder, e.g. "cover.jpg" or { src: "cover.jpg", alt: "…" }; empty = halftone placeholder
                     # placeholder colours: cover: { alt: "cover", c1: "#1d3c8f", c2: "#8fb0ff" }
draft: true
book:
  title: ""          # book or run title (defaults to the post title)
  author: ""         # comics: "Writer · Artist"
  series: ""         # e.g. "The Lantern Cycle, book 1 of 3"
  genre: ""          # "Fantasy · slow-burn · found family" (first part becomes the ghost tag)
  length: ""         # "512 pages · audiobook 17h", comics: "Issues 1–12"
  format: ""         # "Paperback, library copy"
  started: {{ now.Format "2006-01-02" }}
  finished:          # leave empty while reading; days read is calculated
recommend_to: []     # pills, e.g. ["Slow-burn fans"]
glance:              # sidebar "At a glance", in order; the first value is shown in bold
  - { k: "Verdict", v: "" }
  - { k: "Pace", v: "" }
read_next: []        # page paths, e.g. ["/watch/low-orbit"]
---

## What it's about (no spoilers)

## What stuck with me

{{</* takeaway */>}}One-line takeaway.{{</* /takeaway */>}}

{{</* spoiler "Spoilers: the ending" */>}}
…
{{</* /spoiler */>}}

## Would I read the next one?
