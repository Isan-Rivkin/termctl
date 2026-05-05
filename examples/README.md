# termctl examples

Concrete invocations to copy-paste.

## 1. Three Kubernetes log streams in one tab

```bash
termctl exec \
  -- stern -n prod api \
  -- stern -n prod worker \
  -- stern -n prod scheduler
```

Splits the current tab into three horizontally-stacked panes, each tailing a
different deployment.

## 2. Side-by-side process monitors

```bash
termctl --split vertical -- top -- htop
```

Two panes side-by-side. The `exec` subcommand is inferred because `--` is not
a known subcommand.

## 3. Drive panes from a file

```bash
termctl exec --file ./commands.txt
```

Reads `commands.txt` (one command per line, `#` for comments) and runs each
in its own pane. Pipe form also works:

```bash
cat commands.txt | termctl exec --file -
```

## 4. Plan-only (no iTerm2 changes)

```bash
termctl exec --dry-run -- echo first -- echo second -- echo third
```

Prints the parsed plan to stdout and exits 0 without touching iTerm2.
