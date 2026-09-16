---
applyTo: "**/*Tests.cs,**/*Test.cs,**/*.Tests/**/*.cs,**/tests/**/*.cs,**/test/**/*.cs"
---
# Test instructions

Use these rules for test work. Keep tests small, deterministic, and behavior-focused.

Defaults below are for common .NET test stacks. If a repository uses a different stack, use the repo's existing framework and conventions unless they conflict with these instructions.

## Do / Don't (Read First)

### Do
- default to xUnit for test execution
- default to bUnit for Blazor component and Razor page tests
- default to AwesomeAssertions for assertions, do not use FluentAssertions or other assertion libraries without approval
- keep tests in the test project path defined in `PROJECTS.md`
- use bUnit when testing rendered markup, parameters, cascading values, user interaction, validation messages, event callbacks, or conditional UI
- use plain unit tests when logic can be tested without rendering a component
- prefer the simplest test type that verifies the behavior
- test observable behavior through rendered output and callbacks, not component internals
- re-query DOM elements after interactions
- use `InvokeAsync()` for parameter changes and component method calls
- prefer async bUnit interactions such as `ClickAsync`, `ChangeAsync`, `BlurAsync`, and `InputAsync`
- register only the minimal required services in the test context
- mock or fake JavaScript interop, navigation, time, and external services as needed
- prefer targeted assertions on text, attributes, enabled or disabled state, validation messages, CSS classes, and callback results
- prefer extracting complex UI logic into plain C# services or helpers so behavior can be covered with unit tests before adding bUnit coverage
- default to TDD when behavior changes
- keep tests isolated and deterministic
- prefer `TimeProvider` or `FakeTimeProvider`; avoid `Task.Delay` and use time-controlled or event-driven waits/assertions instead
- ensure test names clearly describe the behavior being verified

### Don't
- do not create a separate Razor test project unless repository structure or maintainability requires it
- do not use broad snapshot assertions when targeted assertions are enough
- do not test third-party library internals directly
- do not use live network calls, real external services, or unnecessary filesystem access
- do not put secrets or sensitive data in fixtures or sample inputs
- do not end test names with `Test` or `Async`
- do not include `Test_` in test names
- do not end test names with `_`

## Test project structure

- Organize tests by feature or type, for example:
  - `Components/`
  - `Pages/`
  - `Services/`
  - `Utilities/`
  - `TestDoubles/`

## Regression testing

- For each behavior bug fix, write a failing test first that captures the defect scenario and expected behavior.
- Keep at least one targeted assertion tied to the historical bug symptom.
- Preserve nearby existing behavior checks to reduce regression risk.
- Avoid broad refactors; prefer minimal, behavior-preserving test additions and fixes.
- When the consuming project uses an issue tracker, record its identifier in that project’s convention; otherwise retain a targeted assertion tied to the historical symptom.

## Verification

Use `PROJECTS.md` for project-specific verification paths and commands.
