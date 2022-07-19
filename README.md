# otelpgx

Provides [OpenTelemetry](https://github.com/open-telemetry/opentelemetry-go) 
instrumentation for the [jackc/pgx](https://github.com/jackc/pgx) library.

## Requirements

- Go 1.18 (or higher)
- pgx v5 (or higher)

## Usage

Make sure you have a suitable pgx version:

```bash
go get github.com/jackc/pgx/v5@v5.0.0-alpha.5
```

Create the tracer as part of your connection:

```go
	cfg, err := pgxpool.ParseConfig(connString)
    if err != nil {
        return nil, fmt.Errorf("create connection pool: %w", err)
    }

    cfg.ConnConfig.Tracer = otelpgx.NewTracer()

    conn, err := pgxpool.NewConfig(ctx, cfg)
	if err != nil {
        return nil, fmt.Errorf("connect to database: %w", err)
    }
```

See [options.go](options.go) for the full list of options.