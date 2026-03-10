# GitHub Copilot Instructions for this Repository

## Project Description

This project is an educational website for sharing homework assignments and coding exercises with students. Students can browse, view, and download assignments directly from the portal.

## Project Structure

- [`assignments/`](../assignments/) Each homework assignment is stored in its own subfolder with a consistent structure.
- [`templates/`](../templates/) Reusable templates for new content.
- [`assets/`](../assets/) Contains the website assets including CSS, JavaScript, images, and configuration files.
- [`index.html`](../index.html) The main website page that serves as a static portal for browsing and viewing assignments. Content is configurable via [`config.json`](../config.json) file to dynamically generate assignment lists and details.

## Project Guidelines

- Maintain consistent styling across all pages.
- Keep file and folder names descriptive and organized.

## Educational Standards

When generating content for this project:

- **Learning-focused**: All content should be designed with clear learning objectives and appropriate difficulty levels.
- **Student-friendly**: Use clear, encouraging language that motivates students.

## Goals
- Keep content **student-friendly**, **learning-focused**, and **clear**.
- Preserve the existing site structure and styling.
- Make it easy for educators to add new assignments and for students to browse them.

## When making changes
- Prefer editing or adding content under `assignments/`.
- Maintain consistent formatting and naming conventions.
- Don’t change the build/serving structure (static HTML + config-driven listing).

## When generating new assignment content
- Use the `templates/assignment-template.md` as a guide.
- Ensure the lesson has a clear goal, steps, and a challenge/exercise section.
- Keep the tone encouraging and concise.

## Technical behavior
- `index.html` is the entry point; `config.json` controls which assignments appear.
- Assets live under `assets/` (CSS, JS, images).
- Avoid modifying files unrelated to the assignment content unless asked.
