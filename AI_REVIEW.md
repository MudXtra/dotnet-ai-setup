# AI_REVIEW.md - Pull request and general code change review checklist

Use this checklist before proposing or accepting code changes. Unless target repository guidance or PR templates explicitly vary, use these baseline rules and review conventions.

## Scope

* confirm the change stays within the requested task
* confirm no unrelated refactors or file moves were introduced
* confirm protected projects were not modified unless explicitly requested
* confirm AI tooling/setup changes and feature changes are kept in separate PRs
* distinguish identifying a rule needing revision from authority to silently violate it

## Architecture

* confirm logic is placed in the correct project
* confirm new abstractions are necessary and fit existing patterns
* confirm dependency direction remains appropriate
* confirm no unnecessary dependencies were introduced; prefer dependencies that are free and open source when they exist

## Security and data handling

* confirm no secrets, tokens, passwords, certificates, private URLs, or real connection strings were added
* confirm sensitive data is not logged, exposed, or copied into examples or tests
* confirm configuration changes are safe for local, CI, and production use

## Component and UI rules

* confirm component parameters are auto-properties only
* confirm component parameters are not set through `@ref`
* confirm existing component, UI, and application patterns are preserved unless a change is required
* confirm accessibility remains intact, including keyboard support and ARIA expectations

## Testing

* confirm a focused test was added or updated when behavior changed
* confirm new or updated tests can actually fail (tests that only assert the input you passed prove nothing)
* confirm tests use the repository's native testing frameworks (e.g. bUnit, NUnit, xUnit, AwesomeAssertions) matching existing repo patterns
* confirm tests avoid cached element references across interactions
* confirm tests use async interaction helpers where applicable
* confirm tests do not use unnecessary delays or brittle timing
* confirm test names follow repo naming conventions
* confirm test failures are resolved by fixing root causes, not by weakening, skipping, or deleting valid assertions

## Code quality

* confirm the diff is minimal and readable
* confirm XML `<summary>` docs exist for new public APIs
* confirm no warnings were suppressed to force success

## Verification

* confirm the exact commit SHA being reviewed is stated in the review record
* confirm the review never claims a test, build, or behavior check that was not actually executed
* confirm any suggested commands are targeted to the affected project, not the whole solution, unless explicitly requested
* confirm formatting guidance is scoped to changed files when possible
* confirm suggested code changes are tested against the reproduction before proposing them; if an edge case or environment constraint prevents local testing, state plainly that the suggestion is unverified

## Output expectations and suggestions

* keep feedback brief and actionable
* separate required fixes from optional suggestions, calling out critical defects or regressions explicitly
* suggest concrete code fixes when possible (and how), providing batchable diffs or line-referenced snippets rather than abstract criticism alone
* provide exact verification commands alongside suggested changes in case an AI model or environment does not have native execution tools
* use repository PR templates and standard review formatting by default (see `templates/` for base reference templates)
* do not request unnecessary cleanup outside the task scope
