# AI_REVIEW.md - Pull request and general code change review checklist

Use this checklist before proposing or accepting code changes.

## Scope

* confirm the change stays within the requested task
* confirm no unrelated refactors or file moves were introduced
* confirm protected projects were not modified unless explicitly requested
* distinguish identifying a rule needing revision from authority to silently violate it

## Architecture

* confirm logic is placed in the correct project
* confirm new abstractions are necessary and fit existing patterns
* confirm dependency direction remains appropriate

## Security and data handling

* confirm no secrets, tokens, passwords, certificates, private URLs, or real connection strings were added
* confirm sensitive data is not logged, exposed, or copied into examples or tests
* confirm configuration changes are safe for local, CI, and production use

## Blazor and component rules

* confirm component parameters are auto-properties only
* confirm component parameters are not set through `@ref`
* confirm existing MudBlazor and Blazor patterns are preserved unless a change is required
* confirm accessibility remains intact, including keyboard support and ARIA expectations

## Testing

* confirm a focused test was added or updated when behavior changed
* confirm tests use bUnit, xUnit, and AwesomeAssertions patterns already used in the repo
* confirm tests avoid cached element references across interactions
* confirm tests use async interaction helpers where applicable
* confirm tests do not use unnecessary delays or brittle timing
* confirm test names follow repo naming conventions

## Code quality

* confirm the diff is minimal and readable
* confirm XML `<summary>` docs exist for new public APIs
* confirm no warnings were suppressed to force success
* confirm no unnecessary dependencies were introduced
* confirm hard-coded colors were not added

## Verification

* confirm any suggested commands are targeted to the affected project, not the whole solution, unless explicitly requested
* confirm formatting guidance is scoped to changed files when possible
* confirm the consumer is told about any critical problems that were found

## Output expectations

* keep feedback brief and actionable
* separate required fixes from optional suggestions
* call out critical problems explicitly
* do not request unnecessary cleanup outside the task scope
