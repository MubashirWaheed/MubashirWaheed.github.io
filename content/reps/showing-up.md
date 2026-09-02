---
title: Showing Up
---

> Half the job is showing up. This tracks the days I did.

<!-- MARK A DAY: add one line inside "entries" in the code block below,
     then commit and push.
       date: "YYYY-MM-DD" | study: minutes | gym: 1 or 0 | language: minutes
       note: short text shown on hover -->

<iframe src="/static/showup-frame.html" id="showup-frame" style="width:100%;border:0;min-height:1400px;overflow:hidden;background:transparent" loading="lazy" title="Showing Up tracker"></iframe>

```json showup
{
  "tracks": [
    { "key": "study",    "label": "Study",    "unit": "min", "color": "#2f6f8f", "thresholds": [1, 60, 120, 180] },
    { "key": "gym",      "label": "Gym",      "unit": "",    "color": "#8f4a2f", "thresholds": [1, 1, 1, 1] },
    { "key": "language", "label": "Language", "unit": "min", "color": "#4a7f4a", "thresholds": [1, 20, 40, 60] }
  ],
  "entries": [
    { "date": "2026-08-08", "study": 120, "gym": 1, "language": 30, "note": "Fourier Analysis. Gym. German 30m. Worked on the website tracker." },
    { "date": "2026-08-09", "study": 200, "gym": 0, "language": 15, "note": "Completed React assessment. German 15m. Completed Fourier Analysis."},
    { "date": "2026-08-10", "study": 240, "gym": 0, "language": 15, "note": "Laplace"},
    { "date": "2026-08-11", "study": 60,  "gym": 0, "language": 20, "note": "short on time because of work"},
    { "date": "2026-08-13", "study": 240, "gym": 0, "language": 0, "note": "Network analysis. No time for gym or German." },
    { "date": "2026-08-14", "study": 90,  "gym": 0, "language": 0, "note": " Network Linear ODE" },
    { "date": "2026-08-15", "study": 360, "gym": 0, "language": 20, "note": "Circuit Analysis, Anki deck for language"},
    { "date": "2026-08-16", "study": 360, "gym": 0, "language": 0, "note": "Completed Circuit Analysis" },
    { "date": "2026-08-17", "study": 45,  "gym": 0, "language": 0, "note": "Bode plot started"},
    { "date": "2026-08-18", "study": 300, "gym": 0, "langauge": 0, "note": "completed Bode Plot and started Non Linear Network"},
    { "date": "2026-08-19", "study": 360, "gym": 0, "language": 0, "note": "non linear circuits"},
    { "date": "2026-08-21", "study": 450, "gym": 0, "language": 0, "note": "op amps and started bridge circuits"},
    { "date": "2026-08-22", "study": 0,   "gym": 0, "language": 180, "note": "usage of werden and Anki deck"},
    { "date": "2026-08-24", "study": 240, "gym": 0, "language": 20, "note": "started signal theory"},
    { "date": "2026-08-25", "study": 240, "gym": 0, "language": 20, "note": "convolution in signal theory"},
    { "date": "2026-08-26", "study": 0,   "gym": 0, "language": 240, "note": "created Anki cards for german language"},
    { "date": "2026-08-27", "study": 0,   "gym": 0, "language": 180, "note": "language"},
    { "date": "2026-09-1",  "study": 0,   "gym": 0, "language": 120, "note": "Anki deck"},
    { "date": "2026-09-2",  "study": 360, "gym": 0  "language": 15,  "note": "Get 3 Laplace, Network Analysis"}
 ]
}
```
