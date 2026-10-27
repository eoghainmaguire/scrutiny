# NIST CSF 2.0 reference data

This folder holds an unchanged export downloaded from NIST's CSF 2.0 Reference Tool. Keeping a dated copy means we can work against the same data while building the first checks.

## Where it came from

- File: `nist-csf-2.0-2026-10-27.xlsx`
- Framework: NIST Cybersecurity Framework 2.0, final version published 26 February 2024.
- Downloaded: 27 October 2026.
- [NIST reference tool](https://csrc.nist.gov/Projects/cybersecurity-framework/filters)
- [Download used](https://csrc.nist.gov/extensions/nudp/services/json/csf/download?olirids=all), linked from the [NIST FAQ](https://www.nist.gov/cyberframework/faqs).
- [Published framework, including the Core in Appendix A](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf)

The download is an Excel workbook, even though its address contains `json`. It includes implementation examples and mappings to other frameworks as well as the CSF Core. Its introduction describes it as a user-generated export from the NIST tool, rather than an official NIST publication.

SHA-256 checksum of the saved file:

```text
388efa5248434485c3bbf3911c66bddc752898ddf38d7fbe087e434cb855098e
```

This checksum identifies our exact copy. The download address can return a different export later, so the date and framework version alone aren't enough to identify the file.

## What we checked

The `CSF 2.0` sheet has 106 current subcategories and 79 entries explicitly marked as withdrawn. These were counted from the Subcategory column, not from the mappings in the Informative References column.

For our sample policy:

- `GV.PO-02` is a current subcategory.
- `GV.PO-99` isn't a listed subcategory.
- `GV.PO02` is missing the hyphen used in the identifier format.

## A detail for the first checker

Finding an identifier somewhere in this workbook won't be enough to call it valid. For example, `RS.RP-01` appears as a withdrawn entry, with a note pointing to `RS.MA-01`.

The planned checker should use current subcategories for valid results and flag withdrawn identifiers separately. It should preserve the original reference and leave any replacement decision to the reviewer. Mappings to other frameworks aren't additional CSF subcategories.

No application code or reusable validation engine has been built at this stage. These checks were only to inspect the reference data and confirm our planning examples.
