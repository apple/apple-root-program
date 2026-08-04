# Externally Operated Subordinate CA: information Apple needs

Complete `apple-root-program-eosc-questions.csv` when you need Apple approval to issue a Subordinate CA Certificate, or to cross-sign a CA Certificate, that will be operated by a legal entity distinct from the owner of the issuing parent CA. Section 1.4 of the [Apple Root Program Policy](https://github.com/apple/apple-root-program) requires approval before each such certificate is issued.

## What to do

1. Answer in the `Answer` column, keeping to the shape given in `Answer format`.
2. Answer every `required` row. For a `conditional` row, read `Required when`; if it does not apply, write `Not applicable` rather than leaving the cell blank.
3. If you are requesting more than one certificate, copy the Certificate Details block as described below.
4. Return the file as a reply on your email thread with certificate-authority-program@apple.com. If you have not opened a thread, send it there.

Apple begins review once every required answer is on file. Until then the request waits.

## The columns

| Column | Meaning |
| --- | --- |
| `Section` | Question group. `Cross-Sign Additionals` applies only to a cross-sign. |
| `Certificate` | Which certificate the row is about. `N/A` means the whole submission. |
| `Topic` | Groups related questions. |
| `Question` | The question. |
| `Answer format` | Shape of answer expected. |
| `Required` | `required` or `conditional`. |
| `Required when` | The circumstance that makes a `conditional` row apply. |
| `Answer` | Your answer. |

## More than one certificate

The file arrives with one set of Certificate Details rows, labelled `Certificate 01`. For each additional certificate:

1. Copy every row whose `Section` is `Certificate Details`, as one block.
2. Paste it directly after the existing Certificate Details rows.
3. Change `Certificate 01` to `Certificate 02` on the pasted rows. Use `Certificate 03` for a third, and so on.
4. For a cross-sign, do the same with the `Cross-Sign Additionals` block.

Leave alone:

- **The `N/A` rows.** Do not copy them. They apply to the whole submission and are answered once.
- **The `Section`, `Topic`, `Question`, `Answer format`, `Required`, and `Required when` cells.** Apple matches your answers on those values, so an edited question cannot be matched.
- **The order of the existing rows.** Add copies after them.

Keep one submission in one file.

## Before you return the file

Re-read the Subject Distinguished Name and the SHA-256 fingerprints and confirm they still match the certificate character for character. Spreadsheet and mail applications substitute characters on save: a hyphen becomes an en dash, a straight quotation mark becomes a curly one. Apple records these values and checks the issued certificate against them, so a substituted character means Apple is checking against the wrong value.

## After you return it

Apple confirms receipt. The decision for each certificate, including any conditions attached to an approval, follows on the same thread. Apple does not commit to a turnaround date.
