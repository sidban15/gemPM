---
name: prd-architect
description: Interactive PRD generator that pulls from the RawNotes folder.
---
# Instructions
1. **Initial Step:** List all files inside the `RawNotes/` folder.
2. **Ask the User:** "I found the following notes. Which one should I use for this PRD?"
3. **Wait for Input:** Once the user specifies a file (e.g., `user_interview_v1.md`):
    - Read that file + `vision.txt`.
    - Extract a **Feature Name** for the folder title.
4. **Execution:**
    - Create the directory: `PRD/[Feature-Name]/`.
    - Generate the structured `PRD.md` inside that folder.
5. **Confirmation:** Tell the user: "PRD created successfully at PRD/[Feature-Name]/PRD.md."
