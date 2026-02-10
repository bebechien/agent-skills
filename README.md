# Agent Skills

This repository contains specialized skills for the Gemini CLI agent.

## Available Skills

### Video Game Creator

A comprehensive assistant for video game development, covering world-building, plot design, character creation, writing, and revision.

**Structure:**

-   **World Building**: Establish geography, history, and culture.
-   **Plot Design**: Structure the narrative arc and quests.
-   **Character Development**: Create compelling protagonists and NPCs.
-   **Writing**: Draft dialogue, flavor text, and item descriptions.
-   **Revision**: Refine and polish content.

**Usage:**

To use this skill, install the packaged `.skill` file:

```bash
gemini skills install video-game-creator.skill --scope workspace
```

Then reload your skills in the CLI:

```
/skills reload
```

Once installed, you can ask the agent for help with any stage of game development, such as "Help me design a fantasy world" or "Create a villain for my sci-fi game."
