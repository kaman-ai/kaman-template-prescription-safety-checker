# Prescription Safety Checker

The app of the **Prescription Safety Checker** template in the Kaman marketplace.

Checks every new e-prescription before a pharmacist verifies it: allergies, interactions, duplicate therapy and dose limits against the patient's chart and your formulary. Clear prescriptions go to the verification queue, flagged ones to a pharmacist with a timeout escalation, severe ones are held with the prescriber told. It flags - it never changes or prescribes. Upload your formulary and connect your FHIR gateway at install.

It is installed as a code project of yours when you install the template,
and it is a thin layer: the work is done by the template's agents and
workflow, on your own systems through the connections you chose at install.

## How it is wired

`kaman.app.json` names the agents and workflow the app uses, and the
actions it offers. The ids in this repository are the template's own.
**Install rewrites the file**: each id becomes the id of your installed
copy. Nothing else is rewritten.

The app talks to Kaman only from its server route (`app/api/action/[id]`),
through `@yoctotta/kaman-sdk/app`, with `KAMAN_BASE_URL` and
`KAMAN_API_KEY` — which a Kaman preview injects. The key never reaches the
browser.

## Publishing a new version

Push here, then republish the template pinned to the new commit. Installs
always take the pinned commit, never the tip of `main`.
