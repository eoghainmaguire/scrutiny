# Plan for the first checker

The first checker will take a plain-text policy and check its explicitly labelled NIST CSF 2.0 subcategory references. This is a design note. The checker hasn't been built yet.

## Start with a simple input

For the first version, use one reference per line in this form:

```text
Our security policy is reviewed annually (NIST CSF 2.0: GV.PO-02).
```

The label tells the checker which text to inspect, even if the identifier is badly formatted. Finding unlabelled references, reading PDFs and checking policy meaning can come later.

## Check each reference

1. Read the reference after the label, inside the parentheses. Ignore spaces around it, but keep the original text for the report.
2. Check its format: two uppercase letters, a dot, two uppercase letters, a hyphen and two digits, such as `GV.PO-02`.
3. If the format is wrong, report it as **malformed**. Don't silently fix it.
4. If the format is right, look it up in the saved NIST data. Report a current subcategory as **valid**, an entry marked as withdrawn as **withdrawn**, and an identifier in neither list as **unrecognised**.

Use the Subcategory column in the `CSF 2.0` sheet. Searching the whole workbook could accidentally match an old identifier or a mapping to another framework.

## Expected examples

| Reference | Result | Short explanation |
| --- | --- | --- |
| `GV.PO-02` | Valid | Exists as a current CSF 2.0 subcategory. |
| `GV.PO-99` | Unrecognised | No matching subcategory in the saved data. |
| `GV.PO02` | Malformed | Missing the hyphen before the number. |
| `RS.RP-01` | Withdrawn | The saved data marks it as withdrawn and points to `RS.MA-01`. |

A withdrawn reference should be flagged for review. The checker shouldn't automatically replace it.

## What the report should show

For each reference, show its original text, line number, result and a short explanation. Count lines from 1, including blank lines. Report repeated references at each location so the reviewer can find them all.

Also include the framework version, reference filename and SHA-256 checksum recorded in [the reference data notes](../data/reference/README.md). That will identify the data used for the check.

If no labelled references are found, say "No labelled references found". If the reference file can't be read, report that the check couldn't be completed. Neither situation should be presented as a successful validation.

## When this first version is done

- The sample policy produces the three results in [expected-results.md](../examples/expected-results.md), at the correct line numbers.
- The withdrawn example above is flagged separately from current references.
- Repeated references are reported at each location.
- Text without labelled references gets the no-references message.
- An unreadable reference file produces a clear error.
- Repeating a check with the same text, rules and reference file produces the same findings.

These checks only establish the status of a reference. They won't judge whether a policy addresses the referenced outcome.
