---
title: "{{ (now.AddDate 0 -1 0).Format "January" }} on popiv"
date: {{ .Date }}
{{- $max := 0 }}{{ range site.RegularPages }}{{ with .Params.issue }}{{ if gt (int .) $max }}{{ $max = int . }}{{ end }}{{ end }}{{ end }}
# NEXT ISSUE NUMBER: the highest issue found when this file was created was #{{ printf "%03d" $max }}.
# Check that nothing else claimed #{{ printf "%03d" (add $max 1) }} in the meantime, then keep or change it.
issue: {{ add $max 1 }}
summary: ""          # subtitle under the title and the text on cards
tags: []
featured: false      # true = candidate for the homepage featured slot (newest featured wins)
factcheck: ""        # optional "Fact-check note" callout at the end
why: ""
draft: true
month: "{{ (now.AddDate 0 -1 0).Format "January" }}"
finished: []
dropped: []
next: []
---

A short intro to the month.
