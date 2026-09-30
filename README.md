# BITS Pilani Digital – Advanced Grading Console

A browser-based grading console built for the **BITS Digital CodeForge V1.0** challenge. Instructors upload a marks file, choose a course, adjust grade ranges while watching the mark distribution, and download the final grades as a CSV.

**Live site:** https://jasmeen-1999.github.io/codeforge-grading-console/

> This is a challenge prototype, not an official BITS Pilani Digital grading tool.

## How to use

1. Enter the **instructor name** (required).
2. Upload the marks file (`.xls` or `.xlsx`). Use the **Download a sample file** link if you are unsure about the format.
3. Read the **upload report** and fix any flagged rows if needed.
4. Select a **course**.
5. Adjust the grade ranges. The histogram, statistics, grade counts and boundary lines update live.
6. Click **Finalize & Download**, review the summary, then **Confirm & Download**.

## Marks file format

The first sheet must contain three columns:

| BITS ID | Course | Total Marks |
|---|---|---|
| 2024001 | Maths | 82 |

- The headers `Student's BITS ID` and `Total Marks (out of 100)` are also accepted.
- Marks must be between 0 and 100. Fractional marks are **rounded up** to the next whole number (for example, 80.2 becomes 81).
- Students who did not appear for the exam (NC grade) should not be included.

## Default grade ranges

| Grade | A | A- | B | B- | C | C- | D | E |
|---|---|---|---|---|---|---|---|---|
| Marks | 80–100 | 70–79 | 60–69 | 50–59 | 40–49 | 30–39 | 20–29 | 0–19 |

The top of the scale (A max = 100) and the bottom (E min = 0) are fixed, so no student is left ungraded. All ranges must be continuous with no gaps or overlaps.

## Bugs fixed (Stage 1)

1. Course list showed the same course multiple times.
2. Courses from an earlier file remained after uploading another file.
3. Min and Max statistics were swapped.
4. BITS ID showed `undefined` in the CSV when headers differed.
5. Reset Range gave a console error before a course was chosen.
6. Students went missing from the CSV when A max or E min was changed.
7. Statistics showed `undefined` / `NaN` after returning to the "Select a course" option.
8. The timer stayed frozen after finalizing and loading a new file.
9. Histogram bars overflowed the chart for large classes.
10. The bell curve did not line up with the histogram bars.
11. Fractional marks such as 79.5 received no grade.
12. A console error appeared when the file dialog was cancelled.

The full write-up (reproduction, root cause, fix and test) is in the Bug Fix Log.

## Enhancements (Stage 2)

- **Upload check:** flags missing columns, missing IDs or courses, non-numeric marks, marks outside 0–100 and duplicate BITS IDs.
- **Review before download:** a summary of grade ranges and student counts with a single confirmation.
- **Safer file name and CSV:** files are named like `Maths_Grades_2026-09-30.csv`, and text with commas is quoted correctly.
- **Distribution warning:** a live note appears when over 60% of students fall in one grade.
- **Grade lines on the histogram:** dashed, labelled cut-off lines move as ranges change.
- **Sample file download:** a correctly formatted Excel template.
- **Usability:** phone-friendly layout, labelled inputs for screen readers and a visible keyboard focus outline.


## Run locally

Download `index.html` and open it in a browser. No installation is needed.

## Deployment

Hosted with GitHub Pages from the `main` branch (root folder).
