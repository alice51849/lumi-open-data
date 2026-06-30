# Film stocks reference

A concise reference for well-known photographic film stocks.

**File:** `film-stocks.json`

## Fields

- `name`
- `type`
- `iso`
- `format_notes`
- `look_characteristics`
- `source_url`

Film availability, datasheets, and emulsions can change. Use manufacturer documentation for technical exposure, processing, and archival decisions.

```python
import json

films = json.load(open("film-stocks.json"))["entries"]
fast_bw = [f["name"] for f in films if f["type"].startswith("black") and f["iso"] >= 400]
print(fast_bw)
```

Relevant Lumi Studio app: [PhotoCream](https://apps.apple.com/app/id6781808054).
