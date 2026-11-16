---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
{{- $max := 0 }}{{ range site.RegularPages }}{{ with .Params.issue }}{{ if gt (int .) $max }}{{ $max = int . }}{{ end }}{{ end }}{{ end }}
# NEXT ISSUE NUMBER: the highest issue found when this file was created was #{{ printf "%03d" $max }}.
# Check that nothing else claimed #{{ printf "%03d" (add $max 1) }} in the meantime, then keep or change it.
issue: {{ add $max 1 }}
summary: ""          # subtitle under the title and the text on cards
why: ""              # shown as "Chose it because"
tags: []             # free tags, lowercase: marvel, nintendo, star-wars, fantasy, sci-fi…
featured: false      # true = candidate for the homepage featured slot (newest featured wins)
factcheck: ""        # optional "Fact-check note" callout at the end
draft: true
name: ""             # the film/series name shown big in the card (defaults to the title)
subtype: ""          # ghost tag, e.g. "Sci-fi film" (defaults to kind)
kind: "Film"         # Film | Series | Special
year: {{ now.Year }}
runtime: ""
where: ""
verdict: "watch"     # watch | wait | skip
related: ""          # optional "If you liked this" page path, e.g. "/read/iron-choir"
related_note: ""     # text after the link: "has a similar quiet, patient pace."
---

Three paragraphs max (the build warns if there are more).
