# Highrise Documentation Style Guide

This markdown document outlines the style guidelines for content creation within the Highrise documentation. This guide is dynamic and may be updated periodically. Contributions through issue reporting or pull requests are welcome.

## Types of Content

Documentation content is categorized into four types:

- **Conceptual**: Provides background and explanatory details.
- **Task-based**: Instructive content that guides the user through steps.
- **Reference**: Content that details commands, parameters, and elements of the system.
- **Tutorial**: Practical, step-by-step guides typically for complex processes.

Ideally, separate each content type with a Markdown header to enhance readability and organization.

## Style Conventions

Our content adheres to the [Microsoft Style Guide](https://learn.microsoft.com/en-us/style-guide/welcome/) with specific adaptations noted below. These guidelines are not exhaustive but address frequent style issues:

- **Tense**: Prefer present tense to improve clarity and immediacy.

  - **Incorrect**: You pressed the button, so the cursor will change soon.
  - **Correct**: After you press the button, the cursor changes.

- **Voice**: Use active voice to clarify the subject and action.

  - **Poor**: The list of players is returned.
  - **Improved**: The server returns the list of players.

- **Person**: Use "we" or "our" to denote Highrise collectively and "you" for the reader, minimizing overuse of "you".

  - **Poor**: If you want to build a custom user interface, you can add a container.
  - **Improved**: To build a custom user interface, add a container.

- **Formatting**: Bold key terms and UI elements, use `monospace` for code and paths.

  - **Poor**: It's _very important_ that you click the stop button after running **./script.sh**.
  - **Improved**: It's **important** that you click the **Stop** button after running `./script.sh`.

- **Clarity**: Avoid idioms and colloquialisms to ensure content is accessible and clear to non-native speakers.

  - **Poor**: Publishing in Highrise is a piece of cake.
  - **Improved**: Publishing in Highrise is straightforward.

- **Modality**:
  - Use "can" for ability or permission.
  - Use "might" for possibilities.
  - Use "must" for obligations.
  - Use "should" for recommendations.
  - Avoid "may" due to its ambiguity.

- **Pronouns**: Avoid gender-specific pronouns; use pluralization to remain neutral and inclusive.

  - **Poor**: A player can see his or her inventory.
  - **Improved**: Players can see their inventories.

- **Verb Choice**: Use "select" for options and "click" for buttons.

  - **Poor**: Click and drag to grab the signpost. Then select the **Color** button.
  - **Improved**: Select the signpost and click the **Color** button.

- **Numbers**: Spell out numbers one through nine; use numerals for 10 and above, and always with units.

  - **Poor**: 3 people looked for thirteen files on a six GB hard drive.
  - **Improved**: Three people looked for 13 files on a 6 GB hard drive.

## Linking Strategies

### External Links

For linking to external websites, use standard Markdown links:

- `[Creator Dashboard](https://create.highrise.game/dashboard)`
- `[Unity](https://unity3d.com/)`

### Internal Documentation Links

When linking to internal documentation pages, use relative links including the `.md` extension:

- `[Studio Overview](../pages/learn/studio/basics/overview)`

## Engine Reference Documentation (YAML)

Documentation within `content/en-us/reference/engine/` utilizes YAML. This structured format requires precise indentation and benefits from the following practices:

- **Use of `|` for multi-line strings**: Allows inclusion of multiple paragraphs and code blocks.
- **Categories**: Files are categorized by Classes, Data Types, Enums, Globals, and Libraries.

Editing YAML files typically involves filling out predefined fields such as `summary`, `description`, and occasionally `deprecation_message`. Do not introduce new API elements.

## Images and Media

Use images sparingly to maintain clarity and ease of maintenance. Opt for JPGs for photos, PNGs for screenshots and diagrams, and SVGs for detailed graphical representations.

**Guidelines**:

- Ensure images are under 200 KB.
- Prefer static images over GIFs; use MP4 for video content.
- Use hyphens to separate words in file names (e.g., `example-image.png`).

## Alerts

Use alerts to highlight critical information succinctly:

```markdown
<Alert severity="warning">
This is a beta feature and may change.
</Alert>
```

**Severity Types**:

- **error**: Indicates critical issues.
- **info**: Provides general information and clarifications.
- **success**: Celebrates successful outcomes.
- **warning**: Cautions against potential problems.

This style guide serves to maintain consistency and clarity across Highrise documentation. Follow these guidelines closely to ensure high-quality and accessible content.

