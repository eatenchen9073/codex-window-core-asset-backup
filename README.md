# Codex Window Core Asset Backup

[English](README.md) · [简体中文](README.zh-CN.md)

**A Codex skill for selecting and independently backing up the project assets that matter for recovery.**

Codex and AI Agent projects can accumulate code, source material, exports, and intermediate versions. This skill helps identify what is needed to understand and continue the work, then records the decisions and project history that would otherwise be easy to lose.

For a one-off backup, it prepares two independently usable packages for the same project: a **minimal package** and an **expanded package**. Each package includes its own README, project recap, manifest, and restore guidance. The expanded package adds selected materials with a clear rollback, reuse, or reference purpose.

It can also compare periodic backups, organize batch indexes for multiple projects or work windows, and estimate the new storage used compared with copying the entire project. It does not automatically delete original files or promise exact reproduction on another computer without verification.

> **Version:** 0.5 Beta

## Five categories of core assets

The skill selects assets by the recovery value they preserve. Depending on the project, core assets can include:

1. **Project continuity and decisions** — the project goal, confirmed choices, current state, open tasks, and the context needed to resume work.
2. **Editable sources and dependencies** — authoritative source files, essential inputs, configuration, and tools or dependencies needed to edit the project or regenerate outputs.
3. **Canonical deliverables** — the current user-facing result and essential companions, with approved, candidate, or historical status identified clearly.
4. **Evidence and provenance** — source references, review records, validation results, and checksums that help explain or verify the work.
5. **Rollback points** — a confirmed baseline or pre-change snapshot that provides a useful way to compare or recover from a consequential revision.

The minimal package keeps the smallest complete set needed for the intended recovery level. The expanded package adds selected assets that support a concrete reuse, rollback, or reference need.

## What it does

- **Selects for recovery value.** Keeps the authoritative editable sources, essential inputs and outputs, necessary configuration, and records needed to understand the project.
- **Creates two useful tiers.** The minimal package holds the smallest complete set for recovery and continued editing. The expanded package adds chosen historical baselines, useful intermediate work, exports, or review evidence.
- **Explains important choices.** Records why significant assets were included or omitted and what the expanded-only additions are for.
- **Preserves project context.** Adds a project recap covering the goal, decisions, meaningful milestones, current outputs, and unfinished work. A handoff can be included when a phase is paused.
- **Checks periodic changes.** Compares current core assets with the latest accessible, verified backup and reports when no new backup is needed.
- **Guides batch recovery.** Can create project and window indexes so users can navigate from a work window to its project package and restore steps.
- **States recovery limits.** Describes whether the package supports understanding, viewing deliverables, rebuilding outputs, or continued editable development, and records known setup gaps.

## How to use it

Install or enable the skill in Codex, then invoke it when you want to organize a backup. For example:

- “Create a minimal and an expanded backup package for this project. Show the selected files, estimated package sizes, and known restore limitations before copying.”
- “Compare this project with its latest verified backup. If the core has not changed, report that no new backup is needed.”
- “Review these project windows and prepare a batch index that links each window to its project and recovery package.”

For periodic use, invoke the skill again when you want to check for changes. The skill does not include a timer or schedule by itself.

## Install

Place this repository folder in your Codex skills directory. For a user-level installation on macOS or Linux, the directory is commonly:

```text
~/.codex/skills/codex-window-core-asset-backup/
```

The folder should contain `SKILL.md`. Make sure your Codex client can access the skills directory; refresh or restart it if needed.

## Package contents

A typical one-project backup contains two independent package folders:

```text
project-backup/
├── minimal-package/
│   ├── README.md
│   ├── PROJECT-RECAP.md
│   ├── manifest.json
│   └── selected core assets...
└── expanded-package/
    ├── README.md
    ├── PROJECT-RECAP.md
    ├── manifest.json
    └── selected core assets and useful additions...
```

The expanded package is not a copy of every project file. Each extra item should support a concrete reuse, rollback, or reference need. If no meaningful additions exist, the skill should say so instead of padding the package.

For a batch covering multiple projects or Codex windows, the batch root can include a README, `PROJECT-INDEX.csv`, and `WINDOW-INDEX.csv`, with completed project packages beneath it.

## Storage and cleanup

The skill can estimate how much new storage the selected packages will use and compare that amount with copying the whole source project. This is a comparison of **new backup space**. The original project and earlier backups remain in place, so creating a smaller package does not itself free disk space.

The skill does not delete or clean up source files. Review the backup first; local storage decreases only if you decide the originals are safe to remove and then remove them yourself.

## Restore on another computer

Each package is intended to be transferable and independently usable. Its README describes the project entry point, included files, setup requirements, and known gaps. Recovery may support understanding the project, viewing its deliverables, rebuilding outputs, or continuing editable development.

The actual recovery level depends on the included assets, applications, dependencies, and external services. Unless restoration has been tested in a clean environment or on another computer, the package is not a guarantee of exact reproduction.

## Safety and selection

The default selection excludes credentials, cookies, tokens, `.env` files, unrelated personal files, caches, and reinstallable dependencies. An otherwise excluded item is included only when it is the sole recoverable copy or the user explicitly requests it. The skill copies selected files; it does not move or delete originals.
