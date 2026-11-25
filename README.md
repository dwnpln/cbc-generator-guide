# CBC Generator

A single-file browser tool that builds a Competency-Based Curriculum (CBC) from a TESDA **Training Regulation (TR)** or **Competency Standard (CS)** saved as a Word file (.docx).

Everything runs in your browser. The file is read locally and nothing is uploaded anywhere.

## Quick start

1. Open `CBC_Generator.html` in a modern browser (Chrome, Edge, Firefox, Safari). An internet connection is needed on first load for Bootstrap and the Word reader (mammoth), both loaded from cdnjs.
2. In step 1, choose or drag in the TR or CS (.docx).
3. If the file is a CS, fill in step 3 (see below).
4. In step 2, pick a part. It appears in the preview.
5. Click **Download Word (.doc)** or **Print or save as PDF**.

## What it generates

| Part | Content |
| --- | --- |
| 1 | Sector and qualification |
| 2 | Table of contents (modules by Basic, Common, Core) |
| 3 | Course design: duration, hours per category, description, entry requirements |
| 4 | Course structure: units, modules, learning outcomes, hours |
| 5 | Resources and delivery: tools, facilities, trainer's qualifications, institutional assessment |
| 6 | Modules of instruction: Basic competencies |
| 7 | Modules of instruction: Common competencies |
| 8 | Modules of instruction: Core competencies |

The **Parts 1–5** button generates the front matter in one go.

## TR versus CS

| Source | What it contains | Result |
| --- | --- | --- |
| **TR** | Sections 1–5: units, hours, learning outcomes, methodologies, entry requirements, tools, facilities, trainer, assessment | Every part is filled automatically |
| **CS** | Section 1 (qualification, unit list) and Section 2 (units, elements, performance criteria, knowledge, skills, evidence guide) only | Parts 2 and 6–8 are filled from the file. Hours, methodologies and resources must be entered by hand |

### Working with a CS

When no Section 3–5 data is found, the tool shows a notice and a panel titled **3. Fill in what the CS lacks**. All fields are optional:

- Nominal duration and SIL hours
- Course description (pre-filled from the CS when found)
- Trainee entry requirements, one per line
- Tools, equipment and materials, one per line as `qty | item`
- Trainer's qualifications, one per line
- Institutional assessment
- Hours and methodologies for each unit (open each unit's drop-down)

Anything left empty shows as `n/a` or `0 hours`, and the **Notes** section at the end of each part lists what is missing.

## Editing the parsed data

Under **Edit parsed data (JSON)** you can correct anything the reader got wrong. The panel in step 3 and the JSON stay in sync. Your edits are used as-is the next time you generate a part.

## How the file is read

- Unit titles, codes, descriptors, elements, performance criteria, required knowledge and skills, resource implications and assessment methods come from Section 2.
- Hours and methodologies come from Section 3 of a TR, or from the step 3 panel for a CS.
- A "DRAFT" watermark that leaks into the text is removed automatically.
- Qualifications are recognised by "NC I–IV" or "Level I–IV".

## Known limitations

- Training facilities (Part 5) can only be read from a TR. There is no input for it in the CS panel yet, so it shows `n/a` for a CS.
- Methodologies entered for a CS are one list per unit and appear under every learning outcome of that unit.
- Unit titles that wrap across several lines are joined automatically, but unusual layouts may still need a fix in the JSON editor.
- Download produces an HTML-based `.doc` file that opens in Word. For exact page layout, use **Print or save as PDF**.
- Only `.docx` is accepted. Convert `.doc` files first.

## Privacy

No data leaves your browser. The only network requests are for the Bootstrap stylesheet and the mammoth script.
