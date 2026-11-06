# Retail scheduling solver pack

Configuration archive for the retail scheduling example in the
[Helixor solver tutorial](https://helixor.dev/solver/tutorial/milestone-8.html).

The archive binds the custom problem type `retail_rota` to the shared
`rostering` policy. It contains a solver manifest, one small dataset, and UX
metadata. It does not contain Python, JavaScript, native code, or an optimizer.

## Layout

```text
retail_scheduling-1.0.zip
├── pack.yaml
├── manifests/
│   └── retail_rota.yaml
├── datasets/
│   └── small_store.demo.json
└── ui/
    └── retail_rota.views.yaml
```

`retail_scheduling-1.0.zip` in this repository is that archive. It contains
only those four paths. This README and the license are not part of the upload.

`datasets/small_store.demo.json` is the two-employee problem from the tutorial:
Alice can cover Monday open, and Ben can cover Monday close. `pack.yaml`
publishes it as scenario `small_store`.

`manifests/retail_rota.yaml` declares the five tutorial rules, the generic
form controls, and the `data_schema` for employee and shift records. Required
record fields are in `data_schema`.

`ui/retail_rota.views.yaml` records the input panels and the rostering solution
views described in the tutorial: employees, shifts, eligibility, capacity,
calendar, coverage, hours, and the feasibility certificate. The current Solver
UX does not install a specialized visualization from this file. It uses the
manifest for discovery and forms, and its code registry for a specialized
solution component. When that component is absent, the generic fallback is a
placement table plus the certificate.

## Upload

Send `retail_scheduling-1.0.zip` as raw zip bytes with
`Content-Type: application/zip`. The tutorial shows the validate, upload, and
activate requests. Validation does not activate the pack. Use the bearer token
issued for your account. This repository does not mint a token.

Ask your service operator for the Solver API origin when it differs from the
browser console. A downloaded archive is not activated on a hosted solver until
that API admits it.
