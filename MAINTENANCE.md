# Release checklist

## After every release: fix the creator name type

Zenodo records "Lumi Studio" as a **person**, with the whole name as a family
name. DataCite and OpenAIRE then aggregate this deposit under an author who
does not exist.

The legacy `.zenodo.json` schema has no name-type field, so this cannot be
fixed from the repository — it recurs on every release and has to be corrected
by hand:

1. Open the new record on zenodo.org.
2. Edit → the creator "Lumi Studio" → set name type to **Organizational**.
3. Save. DataCite picks the correction up on its own.

This note lives here rather than in `.zenodo.json`. Zenodo publishes that
file's `notes` field on the record page and passes it to DataCite, so a
maintenance to-do left there is shown to readers as part of the dataset
description — which is exactly what happened to v1.0.0 and v1.1.0.

## Counts

Every count in `README.md`, `.zenodo.json` and `RELEASE_NOTES.md` must be read
out of the JSON, not carried over from the previous release. v1.1.0 shipped
with a README still claiming 28 passport entries while the data held 45, and
a DOI makes that permanent.
