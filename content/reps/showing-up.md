---
title: Showing Up
---


> Half the job is showing up. This tracks the days I did.

<!-- MARK A DAY: add one line inside "entries" in the code block below,
     then commit and push.
       date: "YYYY-MM-DD" | study: minutes | gym: 1 or 0 | language: minutes
       note: short text shown on hover -->

<iframe src="/static/showup-frame.html" id="showup-frame" style="width:100%;border:0;min-height:1400px;overflow:hidden" loading="lazy" title="Showing Up tracker"></iframe>

```json
{
  "tracks": [
    { "key": "study",    "label": "Study",    "unit": "min", "color": "#2f6f8f", "thresholds": [1, 60, 120, 180] },
    { "key": "gym",      "label": "Gym",      "unit": "",    "color": "#8f4a2f", "thresholds": [1, 1, 1, 1] },
    { "key": "language", "label": "Language", "unit": "min", "color": "#4a7f4a", "thresholds": [1, 20, 40, 60] }
  ],
  "entries": [
    { "date": "2026-08-08", "study": 199, "gym": 1, "language": 45, "note": "S-parameters 14:00-16:00. Gym push. German 30m." }
]
}
```
