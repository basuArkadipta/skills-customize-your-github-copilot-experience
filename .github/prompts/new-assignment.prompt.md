---
name: "new-assignment"
description: "Generate a new assignment README.md that follows the project's assignment template"
---

You are given an assignment specification (title, objective, and tasks). Produce a complete `README.md` file that strictly follows the project's assignment template located at `templates/assignment-template.md`.

Rules:
- Use the exact icons and headings from the template: `📘 Assignment:`, `🎯 Objective`, `📝 Tasks`, and `🛠️` for task titles.
- Include a short, descriptive title.
- Write a 1–2 sentence objective describing the learning goal.
- Provide at least two tasks. For each task include `Description` and `Requirements` with specific, measurable bullet points.
- Add example input/output in fenced code blocks when helpful.
- Output only the final markdown content of the `README.md` file (no extra commentary).

Input format (JSON):
```
{
  "title": "...",
  "objective": "...",
  "tasks": [
    {"title": "...", "description": "...", "requirements": ["...", "..."]},
    ...
  ]
}
```

Produce the `README.md` content filled with the provided values.
