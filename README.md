# ts-prune, with false positives handling

To understand this repo, you will only need to:

1. Read [the _tsprune-false-positives.conf_ file](/.ts-prune/artifacts/tsprune-false-positives.conf)
2. Read [the _index.ts_ file](/src/index.ts)
3. Run the following commands:

- `$ npm run ts-prune`
- `$ npm run ts-prune-verbose`

## Config file

### Quirks

The config file can only contain:

- Empty lines (lines containing only spaces/tabs are parsed as empty too)
- Commented lines, starting with a `#`
- Filepaths (one per line)

When you add a file path, just copy and paste the output of ts-prune which is a false positive, including the line number (which will be wildcarded during the sanitizer parsing).

### Flaws

Inline comments like this are NOT supported:

```yaml
src/index.ts:1 - _ # BYPASS
```

Instead, write this:

```yaml
# BYPASS
src/index.ts:1 - _
```
