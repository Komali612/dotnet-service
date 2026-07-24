# dotnet-service

Sample ASP.NET Core 8 minimal API used to exercise the [ci-agent](../ci-agent) pipeline.
One endpoint (`GET /greeting?name=`), xUnit tests (unit + WebApplicationFactory
integration), coverlet coverage in OpenCover format for Sonar.

CI is intentionally thin: `.github/workflows/ci.yml` just calls the shared reusable
workflow in `ci-agent`, which classifies this repo (dotnet), runs
build → test → sonar, and on success pushes `ghcr.io/<owner>/dotnet-service:pr-<n>-<sha>`.

```bash
dotnet test                              # build + tests
dotnet run --project src/DotnetService   # run locally
```

CI agent test: first end-to-end run.
