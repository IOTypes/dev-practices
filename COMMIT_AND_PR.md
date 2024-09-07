## Atomic Commits
* Purpose: Ensures that each commit represents a single, well-defined change.

* Benefits:

  - Easier Review: Smaller commits are easier to understand and review.

  - Better Debugging: If something goes wrong, it's easier to pinpoint the problematic commit.

  - Simplified Rollback: Reversing a single, atomic commit is less risky.

* How to Achieve:
Commit Frequently: Don't wait too long to commit your changes.
Use Descriptive Commit Messages: Clearly convey the purpose of the change.

## PR title Naming
The title of the PR should be `<type>: <what is the ticket>`

Available types:
 - feat: A new feature
 - fix: A bug fix
 - docs: Documentation only changes
 - style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
 - refactor: A code change that neither fixes a bug nor adds a feature
 - perf: A code change that improves performance
 - test: Adding missing tests or correcting existing tests
 - build: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
 - ci: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
 - chore: Other changes that don't modify src or test files
 - revert: Reverts a previous commit

example 
`feat: add Authentication Page`



## PR Should Get Reviewed
* Purpose: Ensures code quality and consistency before merging.
* Best Practices:
  - Prompt Review: Encourage timely review of pull requests.
  
  - Constructive Feedback: Provide helpful suggestions and comments.
  
  - Address Feedback: Make necessary changes based on review comments.
  
  - Use Code Review Tools: Leverage tools like GitHub's built-in review features or VS Code .
