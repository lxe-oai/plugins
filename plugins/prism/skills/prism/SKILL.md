---
name: prism
description: Use when the user wants to work on papers in Prism: find projects, inspect files, read or update LaTeX/text files, add figures or PDFs, download project files, or export whole projects as ZIP archives through the connected Prism app.
---

# Prism

Use the connected Prism app as the primary remote interface when the user wants
to work on a paper or LaTeX project in Prism.

## How to talk about Prism

When the user asks what Prism is or what it can do, answer in product terms
first:

- Prism is a workspace for working on papers,
- organize work into Prism projects,
- inspect the files in a project,
- read or update text files in that project,
- add external figures or PDFs,
- download project files such as figures or PDFs,
- export a whole project as a ZIP archive.

Prefer plain task language:

- “show files in the project”
- “read this file”
- “update this file”
- “download this figure”

## Use the right Prism surface

Use the connected Prism app for headless remote project/file work:

- find or inspect projects,
- list project files,
- read text files,
- create new text files,
- update existing text files,
- add external figures or PDFs,
- download project files,
- export project ZIP archives.

Use a live Prism/browser workflow only when the user explicitly asks to interact
with the live editor, inspect the rendered UI, compile in the live app, or debug
behavior that only exists in the browser surface. Do not choose browser driving
for ordinary remote project/file operations.

## Default workflows

- **Show projects**: use `list_projects`.
- **Open one project**: use `get_project` after the project is explicit.
- **Show project files**: use `list_files` before reading contents.
- **Inspect a text file**: use `read_file` only after the file path is explicit
  or the needed file has been identified from metadata.
- **Create one new text file**: use `create_text_file`.
- **Write generated text**: use `write_text_file`.
- **Add one external figure or PDF**: use `upload_binary_file`.
- **Download one file**: use `download_file`.
- **Download a whole project**: use `download_project_zip`.

Use the narrowest connected-app tool that satisfies the request. Do not read
full file contents when project/file metadata is enough.

## Local folders

The packaged app-backed plugin does not currently provide whole-folder local
sync parity. Do not promise pull/push folder sync, `.prism-sync.json`, or
automatic conflict handling through this plugin surface.

## Project and file model

Treat a Prism project as one remote workspace with two user-visible kinds of
content:

- text files and folders that make up the project tree,
- binary project files such as figures or PDFs.

The user should not need to know the implementation split. Speak in terms of
project folders and files, and use explicit text-file or binary-file operations
only when choosing the right connected-app tool.

## Output discipline

After Prism work, report:

- which project you operated on,
- which files were read, created, updated, or downloaded,
- any failure that still blocks the requested remote operation.

For ordinary successful work, keep the response focused on the project and files
the user asked about.

## Examples

- “Show my Prism projects” -> `list_projects`
- “What files are in this paper?” -> `list_files`
- “Read `main.tex`” -> `read_file`
- “Create `sections/methods.tex`” -> `create_text_file`
- “Update `main.tex` with this revision” -> `write_text_file`
- “Upload `figures/chart.png`” -> `upload_binary_file`
- “Download `main.tex`” -> `download_file`
- “Download this Prism project as a ZIP” -> `download_project_zip`
