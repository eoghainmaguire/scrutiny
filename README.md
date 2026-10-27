# Scrutiny

Scrutiny is an open-source project I'm building to help with reviewing security policies. The first goal is to check whether references to NIST CSF 2.0 are valid.

It's still at the planning stage. There isn't a working tool yet, so everything below is what I plan to build.

## Why I'm building it

Security policies can contain incorrect framework references or references copied from older versions. Checking these by hand can be time-consuming and easy to get wrong.

I want Scrutiny to make those basic checks easier and show what needs a closer look. It's also a way for me to learn more about governance, risk and compliance (GRC) through a practical project.

## Who it's for

The idea is to help GRC analysts, security teams and people who write or review security policies. It could also be useful for students learning how policies relate to security frameworks.

## First version

I'll start with NIST Cybersecurity Framework (CSF) 2.0. The plan is to:

- Take policy text containing CSF subcategory references.
- Check whether the references are in the right format and exist in the official CSF 2.0 data.
- Show which references are valid and which need attention, with a short explanation and the relevant text.
- Keep track of the reference data version used for each check.

These will be rule-based checks, without AI. The same text checked against the same rules and data should give the same results.

## Keeping the scope small

The first version will only check references that are explicitly written in the policy. I'll decide on supported file types and report formats during the design stage. Other frameworks can wait until the basics work.

A valid reference doesn't mean a policy meets the framework's requirements or that an organisation follows the policy in practice. Someone will still need to review the content and supporting evidence. Scrutiny won't certify compliance or replace an audit.

## Ideas for later

Once the reference checks work, I'd like to add:

- A command-line interface (CLI) for running checks.
- A web interface for reviewing policies and results.
- Optional semantic analysis to help assess how policy wording relates to framework outcomes.
- Checks for statements that contradict each other within or across policies.
- Human-review attestations: a record of who reviewed a policy version, what they decided and why.

Any suggested matches or contradictions would still need a person to check them. These are future plans, and the details may change as the project develops.

## References and licence

- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [Apache License 2.0](https://github.com/eoghainmaguire/scrutiny/blob/main/LICENSE)
