# AI_REVIEW.md - Pull request and general code change review checklist

Use this checklist before proposing or accepting code changes. Unless target repository guidance or PR templates explicitly vary, use these baseline rules and review conventions.

## Scope

* confirm the change stays within the requested task
* confirm the change is the smallest possible change to solve the problem
* confirm no unrelated refactors or file moves were introduced
* confirm protected projects were not modified unless explicitly requested
* confirm AI tooling/setup changes and feature changes are kept in separate PRs

## Architecture & dependencies

* confirm logic is placed in the correct project and fits existing patterns
* confirm dependency direction remains appropriate and within repository guidelines if they exist
* confirm no unapproved dependencies were introduced; prefer dependencies that are free and open source when they exist

## Security and data handling

* confirm no secrets, tokens, passwords, certificates, private URLs, or real connection strings were added
* confirm sensitive data is not logged, exposed, or copied into examples or tests
* confirm configuration changes are safe for local, CI, and production use

## Component and UI rules

* confirm component parameters are auto-properties only and never set through `@ref`
* confirm existing component, UI, and application patterns are preserved unless a change is required
* confirm accessibility remains intact, including keyboard support and ARIA expectations
* confirm UI typography and text presentation follow consistent design-system standards:
  * use readable, responsive font sizes and line heights;
  * enforce concise, grammatically correct text with consistent capitalization and punctuation; 
  * allow natural wrapping without clipping, overflow, or excessive line lengths;
  * apply ellipsis only when space is constrained, truncation is appropriate, and the complete text remains accessible. Never truncate critical information, actions, or instructions.

## Testing

* confirm a focused test was added or updated when behavior changed
* confirm tests can actually fail (tests asserting only passed input prove nothing)
* confirm tests follow repository test frameworks and conventions without introducing unapproved libraries
* confirm tests avoid cached element references across interactions and use async interaction helpers where applicable
* confirm tests avoid unnecessary delays or brittle timing
* confirm test failures are resolved by fixing root causes, never by weakening, skipping, or deleting valid assertions

## Code quality

* confirm the diff is minimal, readable, and free of warning suppressions
* confirm XML `<summary>` docs exist for new public APIs

## Verification

* confirm the exact commit SHA being reviewed is recorded
* confirm the review never claims a test, build, or check that was not actually executed
* confirm suggested code changes are tested against the reproduction before proposing; if an edge case prevents local execution, state plainly that the suggestion is unverified

## Output expectations and suggestions

* keep feedback brief and actionable
* separate required fixes from optional suggestions, calling out critical defects or regressions explicitly
* suggest concrete code fixes when possible (and how), providing batchable diffs or line-referenced snippets rather than abstract criticism alone
* provide exact verification commands for any suggested changes so reviewers or models without autonomous tool execution can run them directly
* use repository PR templates and standard review formatting by default (see `templates/` for base reference templates)
* do not request unnecessary cleanup outside task scope
* mention task scope witnessed for items that should have failed review

## Verification commands

When reviewing or suggesting code changes, provide and run the exact targeted commands rather than leaving command discovery to the consumer:

```bash
# Build targeted project
dotnet build <project.csproj> --nologo

# Run focused test
dotnet test <test-project.csproj> --filter "FullyQualifiedName~<TestName>" --nologo

# Run targeted test project with hang detection
dotnet test <test-project.csproj> --no-build --nologo --blame-hang --blame-hang-timeout 30s

# Format changed files only
dotnet format <project.csproj> --include <changed-files>
```
