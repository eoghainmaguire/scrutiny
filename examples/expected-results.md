# First reference-check examples

These are the results we want Scrutiny to produce for `sample-policy.txt`. They are planning examples, not output from a working tool.

| Line | Reference | Expected result | Explanation |
| --- | --- | --- | --- |
| 3 | `GV.PO-02` | Valid reference | This subcategory exists in NIST CSF 2.0. |
| 4 | `GV.PO-99` | Unrecognised reference | The format looks right, but this subcategory does not exist in NIST CSF 2.0. |
| 5 | `GV.PO02` | Malformed reference | The reference is missing the hyphen before the number. |

The expected total is three references: one valid, one unrecognised and one malformed.

For this first example, each reference is explicitly labelled as NIST CSF 2.0. The checker should report the original text and line number, including the malformed reference, without silently correcting it.

A valid reference only means the identifier exists. These checks won't judge whether the surrounding sentence addresses the framework outcome.

If policy text contains no references, the expected result is "No references found", with zero findings. That doesn't mean the policy passed a content review.

Reference source: [NIST CSF 2.0, Appendix A, Policy (GV.PO)](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).
