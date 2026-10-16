================================================================================
COPILOT PROMPTS HANDOVER PACKAGE — ENTERPRISE NL-SQL ASSISTANT v2.1
================================================================================

This folder contains the complete, prompt-only specification package to create, 
audit, and enhance the Enterprise NL-SQL Assistant replica using GitHub Copilot.

NO source code files are included in this folder — strictly structured prompt 
directives, architectural contracts, design tokens, and test scenarios.

--------------------------------------------------------------------------------
FOLDER INVENTORY & PURPOSE:
--------------------------------------------------------------------------------

1. 01_SYSTEM_FLOW_AND_LOGIC_PROMPT.txt
   - Defines the strict 12-step Orchestrator pipeline.
   - Enforces the Smart Complexity Threshold (`_is_simple_query`): simple queries, 
     counts, and scalars auto-execute; only hard/complex queries trigger confirmation.
   - Enforces the 3-column initial table projection rule and zero-LLM AST column 
     mutation (`_handle_column_customization`).
   - Bounded 2-step self-correction loop.

2. 02_FRONTEND_UI_AND_TOPOLOGY_PROMPT.txt
   - Fixes the front page: Google Gemini layout, collapsible Schema Explorer tree.
   - Enforces the IN-STREAM Adaptive Card with in-place SQL `<textarea>` editor 
     and dynamic button ("Confirm & Run Edited Query") — NO modal popups!
   - Enforces the compact inline feedback toolbar (`👍`, `👎`, `•••`) with 
     floating 280px tooltip popover — NO screen-blocking dialogs!
   - Fixes the Observability page (`/observability`): Dynatrace Smartscape SVG 
     Service Flow topology diagram, Dual-Database Diagnostics (live ping test), 
     KPI metric cards, and Chat Turn Deep-Dive Inspector.

3. 03_SCHEMA_LOADING_AND_RESOLUTION_PROMPT.txt
   - Fixes the schema loading defect!
   - Explains why schema failed: enterprise tables reside in the custom `poc` 
     schema (not `public`).
   - Specifies multi-schema dynamic discovery (`information_schema.schemata`), 
     PostgreSQL driver `search_path` injection (`-c search_path=poc,public`), 
     and value-aware categorical sampling (distinct count <= 20).

4. 04_COPILOT_AGENT_TEST_AND_ENHANCEMENT_PROMPT.txt
   - Complete 10-Scenario Verification & Self-Enhancement Test Suite.
   - Feed this to GitHub Copilot to automatically audit the codebase, detect 
     discrepancies, and patch the code until all 10 scenarios pass.

5. 05_EXACT_DESIGN_SYSTEM_ICONS_AND_ANIMATIONS.txt
   - Comprehensive Design System specifications:
     * Complete Light and Dark theme color hex palettes and CSS variables.
     * Exact CSS Keyframe animations (`@keyframes flow-smooth`, `pulse-subtle`, 
       `popoverFadeIn`, `cardFadeIn`, `spin`).
     * All 13 raw production SVG icons (brand logo, send arrow, quote, copy, 
       thumbs up/down, three dots, code brackets, play run, cancel, CSV tray, 
       search glass, ping lightning).
     * Exact component styling for feedback popover, in-stream adaptive card, 
       and data tables.

--------------------------------------------------------------------------------
RECOMMENDED EXECUTION SEQUENCE WITH GITHUB COPILOT:
--------------------------------------------------------------------------------

STEP 1: Fix Database Schema Loading
- Open Copilot Chat in your target environment.
- Paste: `03_SCHEMA_LOADING_AND_RESOLUTION_PROMPT.txt`
- Let Copilot patch `schema_service.py` and `session.py`.

STEP 2: Fix Backend Pipeline & Orchestrator Logic
- In Copilot Chat, paste: `01_SYSTEM_FLOW_AND_LOGIC_PROMPT.txt`
- Let Copilot patch `orchestrator.py` (complexity check, 3-column projection, AST column customization).

STEP 3: Apply Exact Color Palette, Animations & Raw SVG Icons
- In Copilot Chat, paste: `05_EXACT_DESIGN_SYSTEM_ICONS_AND_ANIMATIONS.txt`
- Let Copilot inject the exact CSS variables, keyframe animations, and raw SVGs into `styles.css` and `index.html`.

STEP 4: Fix Frontend UI Layout & APM Topology Flow
- In Copilot Chat, paste: `02_FRONTEND_UI_AND_TOPOLOGY_PROMPT.txt`
- Let Copilot patch `index.html`, `app.js`, and `observability.html`.

STEP 5: Run Verification & Auto-Enhancement
- In Copilot Chat, paste: `04_COPILOT_AGENT_TEST_AND_ENHANCEMENT_PROMPT.txt`
- Copilot will review all 10 test scenarios, verify compliance, and output any 
  final refinements.
================================================================================
