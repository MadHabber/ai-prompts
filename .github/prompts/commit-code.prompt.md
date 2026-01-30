---
agent: agent
description: This prompt is used to generate commit messages for code changes based on the provided diffs.
model: Claude Sonnet 4.5 (copilot)
tools: [read, edit, execute, agent]
---

When this prompt is used, follow these instructions:

1. Check the git status to determine if there are any unstaged or staged changes.
1. If there are no staged changes, respond with a message indicating that there are no changes and that the user should stage the changes they want to commit before generating a commit message.
1. Offer to run git add to stage all changes if the user agrees.
1. If there are staged changes, run git diff on the staged changes to get the diffs.
1. Evaluate the changes and generate a concise and descriptive commit message.
1. The commit message should accurately reflect the modifications made in the code, including any new features, bug fixes, or improvements.
1. Ensure the message is clear and follows best practices for [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/). Conventional commit format: <type>(<scope>): <subject> \n\n<body>\n\n<footer>
1. Where <type> is one of the following: feat, fix, docs, style, refactor, perf, test, chore.
1. Where <scope> is optional but can be used to specify the area of the code affected (e.g., component name, module name).
1. Where <subject> is a brief summary of the changes made (max 50 characters).
1. Where <body> is an detailed description of the changes, including the motivation and context (max 72 characters per line).
1. Where <footer> is optional and can include any relevant issue references.
1. Return only the commit message as a bash command in the following format:

```bash
git commit -m "<commit-message>"
```

1. Do not include any explanations or additional text outside of the bash command.
1. Ensure the commit message is properly escaped to be used in a bash command.
1. After displaying the commit command, offer to execute the command to create the commit.
