# Project boundaries

## First-use project map workflow
PROJECTS.md is a maintained map of verified facts, not a task list or source of new permission. Inspect existing projects first and record the target SDK/global.json policy, solution path, roles, test mapping, protected areas, and commands verified against the created project. For an empty repository, propose the smallest Blazor, MudBlazor, or MVC layout matching the chosen application and obtain approval for material structure decisions. UI, data, and test roles may be `N/A`; never create a project merely to satisfy a placeholder. Never record secrets, real connection strings, or sensitive data.

## Files and paths
- {{SOLUTION_NAME}} is the solution file/path
- {{UI_PROJECT_PATH}} owns UI/components/pages/assets/interaction logic; N/A is allowed
- {{DATA_PROJECT_PATH}} owns persistence/services/data access; N/A is allowed
- {{TEST_PROJECT_PATH}} owns bUnit/xUnit tests; N/A is allowed
- {{PROTECTED_PROJECT_PATHS}} allows N/A; do not edit unless explicitly instructed.

## Verification prerequisites and evidence
Run commands from the repository root unless a documented command names another working directory. Before running a command, use verified project facts for the target SDK/global.json policy, project or test-project path, configuration, and test runner. Run a focused test before its full test project when it applies; `--no-build` is valid only after a successful matching build. Use broader test-project, solution, or cross-project validation only when the change, dependency, shared setting, or solution wiring justifies it.

In the final report, name every command actually run and its outcome. Name relevant checks not run, explain why they were not run or not applicable, and never imply a build or test ran when this project map has no runnable target.

## Targeted Verification
- Use targeted verification against <project.csproj> unless broader validation is explicitly requested.
- Prefer focused test execution before running the full test project.

```text
dotnet clean <project.csproj>
dotnet build <project.csproj> --nologo
dotnet test <project.csproj> --no-build --nologo --blame-hang --blame-hang-timeout 30s
dotnet test <project.csproj> --filter "FullyQualifiedName~<test name>" --no-build --nologo --blame-hang --blame-hang-timeout 30s
dotnet format <project.csproj> --include <changed files>
```

## Targeted commands

```text
dotnet build <project.csproj> --nologo
dotnet test <project.csproj> --no-build --nologo --blame-hang --blame-hang-timeout 30s
```
