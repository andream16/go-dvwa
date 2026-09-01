# Development container

This container provides the Go, CGO, Node.js, and Python tooling needed to run
security scanners against this intentionally vulnerable application. It does
not start the web server, expose port 8080, or configure Sqreen credentials.

Use the Ona tasks to download the pinned Go modules, run the test suite, and
attempt the repository's normal instrumented build. The build remains an
intentional validation of the historical source and dependencies; do not
remediate application vulnerabilities or update dependencies as part of
environment setup.

## Validation

Validated on September 1, 2026 with Go 1.27.0, Node.js 24.20.0 LTS, and
Python 3.12.14. `go mod download` and `go test ./...` succeed.

The normal `make` build compiles the historical Sqreen instrumentation tool,
then fails when that tool instruments the Go 1.27 runtime:

```text
$WORK/b010/sqreen.go:5:2: could not import runtime/internal/atomic (open : no such file or directory)
make: *** [Makefile:8: dvwa] Error 1
```

This is a compatibility failure between the historical instrumentation and a
modern Go runtime. The application source and pinned dependencies are left
unchanged intentionally.
