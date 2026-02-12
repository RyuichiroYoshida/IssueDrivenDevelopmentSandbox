# CLAUDE.md

## Project Overview

**IssueDrivenDevelopmentSandbox** is a Go application that visualizes GitHub commit history (contribution graphs) for multiple users in a single dashboard, with automated weekly/monthly MVP recognition based on commit activity. Documentation and code reviews are conducted in Japanese.

- **Module:** `github.com/RyuichiroYoshida/IssueDrivenDevelopmentSandbox`
- **Language:** Go 1.25.5
- **Status:** Early MVP stage

## Repository Structure

```
/
├── main.go              # Application entry point
├── go.mod               # Go module definition (no external deps yet)
├── .coderabbit.yaml     # CodeRabbit AI review config (Japanese, assertive profile)
├── .gitignore           # Standard Go gitignore
└── README.md            # Product requirements and MVP use cases (Japanese)
```

## Build & Run Commands

```bash
# Run the application
go run main.go

# Build a binary
go build -o app main.go

# Run tests (when they exist)
go test ./...

# Run tests with coverage
go test -coverprofile=coverage.out ./...

# Format code
go fmt ./...

# Vet code for issues
go vet ./...
```

## Development Workflow

### Branching

- Primary branches: `main`, `develop`
- CodeRabbit auto-reviews PRs targeting `main` and `develop`

### Code Review

This project uses **CodeRabbit** for automated AI code reviews configured with:
- Language: Japanese (`ja-JP`)
- Review profile: `assertive`
- Auto-review enabled for non-draft PRs to `main` and `develop`
- Auto-apply labels enabled

### Commit Message Convention

Existing commits follow the pattern: `add: <description in Japanese>`

Examples from history:
- `add: README.mdへMVPの追加`
- `add: main.go init`
- `add: go.mod init`

Use the prefix format `<action>: <description>` for commit messages.

## Key Conventions

1. **Language:** Project documentation (README, PR descriptions) is written in Japanese. Code and comments follow standard Go conventions in English.
2. **Go standards:** Follow standard Go project conventions — `go fmt`, `go vet`, and idiomatic Go style.
3. **No external dependencies yet** — the project currently uses only the Go standard library.
4. **Environment variables:** `.env` files are gitignored. Never commit secrets or API keys.
5. **No CI/CD pipeline configured yet** — validate changes locally with `go build`, `go vet`, and `go test ./...` before pushing.
6. **No linter configuration yet** — when adding one, prefer `golangci-lint`.

## MVP Use Cases (Summary)

1. **Dashboard** — Display multiple GitHub users' commit history in one view, sorted by commit count (7-day/30-day).
2. **Automated Awards** — Weekly cron job selects top 3 contributors as MVPs with badge recognition.
3. **User Management** — Add/remove monitored GitHub usernames with GitHub API validation.
