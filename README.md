# sample-reqif-polarion

Public ReqIF samples in the shape of Siemens Polarion exports, with the
**fidelity receipt** [Traceo](https://traceo.cloud) writes when it reads them.

> **Read this first.** At least one file here is *shaped*: hand-written to resemble an export from Siemens Polarion, not produced by it. A clean read of a shaped file shows that Traceo reads that shape. It does not show that Traceo reads what the tool really emits.

## Files

| File | Kind | Source | Licence | sha256 (prefix) |
|---|---|---|---|---|
| `polarion_anonymized.reqif` | **export**: produced by the tool | [`strictdoc-project/reqif`](https://github.com/strictdoc-project/reqif/blob/b44fc51/tests/integration/reqif_software/Polarion/01_anonimized_example/sample.reqif) @ `b44fc51` | Apache-2.0 | `1f9169075c40dd21` |
| `polarion_shaped.reqif` | **shaped**: hand-written to look like the tool's export, *not* produced by it | [`jackhale98/sysml-web`](https://github.com/jackhale98/sysml-web/blob/cddbd21/src/lib/dataio/fixtures/reqif/polarion.reqif) @ `cddbd21` | Apache-2.0 OR MIT | `f6d5b382eaea2d65` |

- `polarion_anonymized.reqif`: An anonymised export from Polarion's ReqIF Roundtrip (tool name renamed `Ppp`).
- `polarion_shaped.reqif`: Hand-written in the shape of a Polarion export. Polarion did not produce it.

Each file is copied byte-for-byte from the repository named and is unedited. Check it against the sha256.

## What Traceo kept

Traceo writes a receipt before it imports anything. The receipt counts every class of item **in**
the file and **kept**. It names every item it did not keep, with a reason code. A file with nothing
in it gets the verdict `vacuous`, never `clean`.

### `polarion_anonymized.reqif`

Verdict: **clean**, every item in the file was kept.

| Class | In the file | Kept |
|---|---:|---:|
| objects | 101 | 101 |
| headings | 43 | 43 |
| attributes | 462 | 462 |
| hierarchy nodes | 101 | 101 |

Full receipt: [`receipts/polarion_anonymized.reqif.receipt.json`](receipts/polarion_anonymized.reqif.receipt.json)

### `polarion_shaped.reqif`

Verdict: **lossy**, some items were not kept, and every one of them is named below.

| Class | In the file | Kept |
|---|---:|---:|
| objects | 4 | 4 |
| headings | 1 | 1 |
| attributes | 21 | 21 |
| enumeration values | 6 | 6 |
| link types | 3 | 2 |
| links | 3 | 2 |
| hierarchy nodes | 4 | 4 |

Not kept, grouped by reason:

| Class | Reason | Count | Example detail |
|---|---|---:|---|
| link types | `dangling_link` | 1 | every link of this type was dangling |
| links | `dangling_link` | 1 | TARGET names no imported object |

Full receipt: [`receipts/polarion_shaped.reqif.receipt.json`](receipts/polarion_shaped.reqif.receipt.json)

These receipts were written by Traceo's ReqIF importer at commit `90cfc15` on 2026-11-03.

## Try it

[Sign up](https://app.traceo.cloud/signup), open Import and choose a file from this repository. Traceo
shows its receipt before anything is written.

## Names

Siemens Polarion is a trademark of its owner. It is named here only to describe the file. Traceo is not
affiliated with or endorsed by its owner.

## Licence

The `.reqif` files are third-party and keep their upstream licence. The texts are in
[`LICENSES/`](LICENSES/). The README and the `receipts/` are © Traceo, released under the MIT
licence in [`LICENSE`](LICENSE).
