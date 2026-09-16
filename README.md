# dotnet-ai-setup

An opinionated starting template for **AI-assisted .NET development**, focused on **Blazor, MudBlazor, and ASP.NET Core MVC**.

Start a repository with a consistent set of instructions for how AI should work in your project: where code belongs, which conventions to follow, how to test changes, and what to check before calling the work complete.

This is not a complete application or a `dotnet new` template. It provides the repository guidance and configuration that surround your application. You supply the project, its requirements, and its boundaries.

## Why use it?

AI works better when it does not have to rediscover your project or guess your expectations on every task.

This template gives you a starting point for:

- Keeping changes focused and consistent with your architecture.
- Giving AI the project paths and commands it needs to work with less supervision.
- Following test-driven development for behavior changes.
- Reviewing code for correctness, accessibility, security, and maintainability.
- Keeping sensitive data and external databases outside ordinary AI development work.

The defaults reflect the technologies and practices used by the author. They are intentionally opinionated—not an attempt to prescribe the right setup for every .NET project.

## Getting started

1. **Create your repository** and copy the starter files from this repository into it.
2. **Create or add your application and test projects.** Use the solution structure that fits your application.
3. **Configure `PROJECTS.md`** with your actual project paths, responsibilities, protected areas, and verification commands.
4. **Review the defaults** in `AGENTS.md`, the test instructions, `.editorconfig`, and `Directory.Build.props`. Adapt them to your project before relying on them. Check file-header ownership and licensing as well.
5. **Check configuration placement.** The supplied build and editor configuration lives at repository root and applies to source and test projects beneath it and preserve any existing configuration.
6. **Keep nullable and warnings-as-errors enabled for new projects; document intentional exceptions in `PROJECTS.md`.**
7. **Run your documented build and test commands**, then commit the configured starting point.

You can ask AI to inspect your solution and draft `PROJECTS.md`. Review the result—especially project responsibilities, protected paths, and commands—before using it as the project map.

## What is included?

| File | Purpose |
| --- | --- |
| `AGENTS.md` | Working rules, development conventions, boundaries, and completion expectations. |
| `PROJECTS.md` | Your repository's project map and targeted verification commands. |
| `AI_REVIEW.md` | A checklist for reviewing changes before submission. |
| `CLAUDE.md` | Loads the shared repository instructions, project map, and review checklist for Claude Code. |
| `.github/copilot-instructions.md` | Directs GitHub Copilot to the shared repository guidance. |
| `.github/instructions/tests.instructions.md` | Testing conventions and regression-test guidance. |
| `.github/pull_request_template.md` | A consistent structure for describing and checking changes. |
| `src/.editorconfig` | Formatting and code-style preferences. |
| `Directory.Build.props` | Shared .NET build settings for projects within its scope. |
| `.gitignore` and `.gitattributes` | Source-control defaults for .NET development. |

### Choosing an assertion library
AwesomeAssertions is the default. A project choosing Shouldly must update the default in `.github/instructions/tests.instructions.md` and `AI_REVIEW.md`, add the selected library via its normal dependency workflow, and keep one consistent default per test project.

The testing guidance favors **xUnit**, **bUnit for Blazor component tests**, and **AwesomeAssertions**. Adapt it to the frameworks your project actually uses; MVC tests do not require bUnit.

## Make `PROJECTS.md` yours

`PROJECTS.md` connects the general instructions to your actual application. It is not a list of tasks—it tells AI where and how to work.

Replace every placeholder with useful project information:

- The solution and relevant project paths.
- What belongs in each project.
- Areas that require explicit permission to change.
- Which test projects cover the affected code.
- The commands needed to build, test, and verify changes.

Keep it concise and update it when the project structure or commands change. Do not put credentials, real connection strings, or sensitive application data in it.

A well-maintained project map lets you describe the outcome you want without explaining the repository from scratch each time.

## Working with AI

Once the template is configured, give your AI tool a concrete task and the expected outcome. Ask it to follow `AGENTS.md`, use `PROJECTS.md` to find the right projects and commands, and check its changes against `AI_REVIEW.md`.

For a multi-step task you want completed without routine stage pauses, explicitly request end-to-end execution within the documented boundaries.

Repository instructions are guidance, not a security sandbox. Tool support for discovering instruction files varies, so confirm your AI tool is loading the relevant guidance. Review the resulting changes and verification evidence before accepting them.

The external-database boundary is defined in [AGENTS.md](AGENTS.md#external-database-boundary). Development and tests should use permitted local, synthetic data—not external databases or copies of real customer or production data.

## Using the files in an existing repository

Starting a new project is the primary use, but you can also adapt these files to an existing repository. Review and merge its existing instructions and configuration rather than assuming the template should replace them.

Copy the files you need manually, preserve your repository-specific settings, and configure `PROJECTS.md` with the existing project structure and commands.

## License

This template is provided under the [MIT License](LICENSE).
