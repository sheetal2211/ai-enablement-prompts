## Overview

This prompt chain guides an AI agent through a series of structured steps to extract meaningful insights from a codebase. It is capable of:

- Identifying Context - the technology stack, major frameworks, build tools, architecture, coding style used
- Providing general guidelines based on the context identified 
- Mapping out file structure and pattern, inferring architecture, patterns to follow and patterns to avoid for every module
- Generating contribution guidelines for future code contributions

The final output, `{final_output_file}.md` (the name of this file is a parameter that must be passed into the AI Agent), serves as a high-level onboarding and guidance document that aligns AI-generated code with your project's existing conventions and design.

## Usage

To use this prompt chain, write something similar to the following in your agent, be sure to modify the parameters at the top accordingly:

```
{output_folder} = .results
{final_output_file} = /.github/copilot-instructions.md

You are assisting with generating a {final_output_file} file using a multi-step prompt chain.

1. Open this repository on GitHub: https://github.com/sagarwal062717/ai-enablement-prompts
2. Navigate to the `/understanding-code/instruction-generation` folder within the repo.
3. Review all the prompt files in this folder WITHOUT executing them. 
    - This will help you understand the full scope of the prompt chain.
4. Confirm you have a full understanding of the prompt chain sequence.
5. Once you're familiar with the flow, begin executing the prompts in numerical order:
    - 1-determine-context.md
    - 2-general-guidelines.md
    - 3-file-structure-and-patterns.md
    - 4-contribution-guidelines.md
6. For each step, output results into a corresponding `{output_folder}/` folder.
    - Mirror the step’s filename e.g., `1-determine-context.md` > `{output_folder}/1-determine-context.md`.

Stop ONLY when:
    - All `instruction-generation` steps are complete
    - A full `{final_output_file}` can be generated.
```

## Agent Capabilities

The AI agent executing this prompt chain is expected to support the following capabilities:

- Reading and writing individual files
- Reading and writing entire folders
- Analyzing code structure, file organization, and implementation patterns
- Identifying and understanding technology stacks, frameworks, and libraries
- Generating structured instruction files based on project analysis

## Parameters

This prompt chain is expected to be provided the following:

- {output_folder} - A path to the folder where generated instruction files will be saved (e.g., `.results/`)
- {final_output_file} - A file which combines all the work that's been done into a single place eg., `/.github/copilot-instructions.md`)

### Copilot
- {output_folder} - `.results/`
- {final_output_file} - `/.github/copilot-instructions.md`

## Execution

When given an {output_folder}, the AI agent will perform the following steps, reading each file and following it's instructions in order:

- [./1-determine-context.md](./1-determine-context.md)
    - Analyzes the codebase to identify the technology stack, frameworks, and libraries being used
- [./2-general-guidelines.md](./2-general-guidelines.md)
    - Provide general guidelines based on the context identified
- [./3-file-structure-and-patterns.md](./3-file-structure-and-patterns.md)
    - Mapping out file structure and pattern
- [./4-contribution-guidelines.md](./4-contribution-guidelines.md)
    - Generates style guidelines and coding standards based on existing code patterns

Each prompt should be provided with the {output_folder} parameter to ensure consistent output location.