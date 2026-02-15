# Gemini PM Agent: README

## 1. Overview

This document provides a comprehensive overview of the Gemini Product Manager Agent's persona, capabilities, project structure, standard operating procedures, and operational guardrails.

The agent's core persona is an **Elite Technical Product Manager**. Its primary mission is to transform "vague ideas" into "shippable Jira tickets" for complex financial services, specializing in bridging the gap between traditional core banking (Savings, Checking, LOC) and modern crypto wallet ecosystems.

The agent is designed to work within a specific project structure, leveraging a set of specialized skills and commands to streamline the product management lifecycle.

## 2. Folder Architecture

The project is organized into the following key directories:

-   **Root Directory**:
    -   `vision.txt`: The "North Star" file containing the high-level product vision. The agent consults this file to ensure all generated requirements align with the core strategy.
    -   `nodes.md`: A "System Map" document, useful for architectural overview.

-   `RawNotes/`: This is the "Inbox" for all raw inputs, research logs, and brain dumps. It contains unstructured data such as interview transcripts, brainstorming notes, market research, and technical specifications.

-   `PRD/`: This is the primary output directory for structured requirements.
    -   Every feature must have a dedicated sub-folder (e.g., `PRD/[Feature-Name]/PRD.md`).
    -   `PRD/JiraTickets/`: Contains sub-folders for different engineering personas (Customer/, CoreBanking/, AdminOps/) where final, formatted Jira tickets are stored.

-   `skills/`: This directory contains the definitions for the agent's specialized sub-routines (skills). Each skill has a `SKILL.md` file that outlines its specific instructions and capabilities.

-   `.gemini/`: This folder contains the agent's configuration, including command definitions (`.toml` files) that expose the agent's skills to the user.

## 3. Specialized Skills

The agent executes logic via the following skills located in `.gemini/skills/`:

-   `prd-architect`: Processes raw notes into structured PRDs, utilizing Mermaid.js for diagrams.
-   `market-intel`: Performs Google Search research on features and 2026 regulations.
-   `backlog-architect`: Converts PRDs into persona-mapped Markdown Jira tickets.
-   `jira-bridge`: (Planned Final Step) Designed to connect to the Jira MCP server to create tickets. This functionality is aspirational and not yet implemented.
-   `pm-orchestrator`: Manages batch-processing of multiple files.
-   `regulatory-intel`: Performs regulatory research for the US and Canada.

## 4. Standard Operating Procedure: GemPM-Start

When triggered with a "Start" command (e.g., through an orchestration command), the agent follows this sequence strictly:

1.  **Ingest State**: Reads `vision.txt` and `nodes.md`. Reads all existing files in `RawNotes/`.
2.  **Intelligence Phase**: Uses `market-intel` for high-level feature UX and regulatory research. Saves findings to `RawNotes/Research_Update.md`.
3.  **Synthesis**: Re-reads all updated files in `RawNotes/` to ensure a unified context.
4.  **Drafting**: Triggers `prd-architect` to generate a comprehensive PRD in a new feature sub-folder.
5.  **Architecting**: Triggers `backlog-architect` to generate tickets within the Persona sub-folders under `PRD/JiraTickets/`.
6.  **Reporting**: Creates `PRD/DOC_SUMMARY.md` indexing all generated files.

## 5. Operational Guardrails

-   **Check Vision**: Always verifies against `vision.txt` (account types: Savings, Checking, LOC; and Commission Schedules).
-   **Diagrams**: Uses Mermaid.js for all workflow diagrams (e.g., Liquidity Sync, Buy/Sell Flow).
-   **Confirmation**: Must ask for explicit confirmation before triggering `jira-bridge`.
-   **Technical Accuracy**: Uses LaTeX for complex financial formulas (e.g., interest or commission calculations).

## 6. Cheatsheet: Quick Command Reference

For a detailed explanation, refer to the "7. Available Commands" section.

| Command                            | Description                                      |
| :--------------------------------- | :----------------------------------------------- |
| `pm prd <feature-name>`            | Refines notes into a structured PRD.             |
| `pm jira <feature-name>`           | Generates Jira-ready syntax from a PRD.          |
| `research market <feature-name>`   | Performs competitive market research.            |
| `research regulatory <topic>`      | Performs regulatory research (US & Canada).      |

## 7. Available Commands

The following commands are configured in the `.gemini/commands/` directory and leverage the specialized skills:

-   `pm prd <feature-name>`
    -   **Description**: Refines messy notes from `RawNotes/` into a structured PRD using the `prd-architect` skill.
    -   **Action**: Reads a selected file from `RawNotes/` and `vision.txt`, then creates a new folder `PRD/<feature-name>` containing a `PRD.md` with a Problem Statement, User Stories, Technical Constraints, and a Mermaid Flowchart.

-   `pm jira <feature-name>`
    -   **Description**: Generates Jira-ready syntax for a specific feature using the `backlog-architect` skill.
    -   **Action**: Reads the `PRD.md` for the given feature, generates 5 User Stories with Acceptance Criteria, and saves them to `PRD/<feature-name>/JIRA_DRAFT.md` (or directly into persona-mapped sub-folders if the `backlog-architect` skill is updated to do so).

-   `research market <feature-name>`
    -   **Description**: Performs competitive research using Google Search and the `market-intel` skill.
    -   **Action**: Analyzes top competitors for the feature, compares their pricing and key offerings, and identifies a "Gap in the Market." The output is saved to `PRD/<feature-name>/competitor_analysis.md` (or `RawNotes/Research_Update.md` as per SOP).

-   `research regulatory <topic>`
    -   **Description**: Performs regulatory research for a given topic in the US and Canada using the `regulatory-intel` skill, saving output to `RawNotes/`.
    -   **Action**: Runs the `regulatory-intel` skill to find and summarize relevant regulatory documents for the specified topic, saving the output to `RawNotes/regulatory_research_[topic_slug].md`.

-   **Note**: The `jira-bridge` (a planned feature) and `pm-orchestrator` skills are typically invoked as part of the `GemPM-Start` SOP or other internal processes, rather than directly as user-facing commands.

## 8. Setup & Configuration

To get started with the Gemini PM Agent:

1.  **Define Your Vision**: Edit the `vision.txt` file to reflect your core product strategy and objectives.
2.  **Populate `RawNotes/`**: Add your own text files containing project ideas, interview notes, or any other source material.
3.  **Run the Commands**: Execute the available commands as described in section 6 to begin processing your notes into structured product documents and Jira tickets.
4.  **Review Outputs**: Check the `PRD/` directory for the generated artifacts.

## 9. Agent Workflow: GemPM-Start

The agent follows a strict Standard Operating Procedure when a "Start" command (e.g., through an orchestration command) is triggered:

1.  **Ingest State**: Reads `vision.txt`, `nodes.md`, and all existing files in `RawNotes/`.
2.  **Intelligence Phase**: Uses `market-intel` for high-level feature UX and regulatory research, saving findings to `RawNotes/Research_Update.md`.
3.  **Synthesis**: Re-reads all updated files in `RawNotes/` to ensure a unified context.
4.  **Drafting**: Triggers `prd-architect` to generate a comprehensive PRD in a new feature sub-folder.
5.  **Architecting**: Triggers `backlog-architect` to generate tickets within the Persona sub-folders under `PRD/JiraTickets/`.
6.  **Reporting**: Creates `PRD/DOC_SUMMARY.md` indexing all generated files.
