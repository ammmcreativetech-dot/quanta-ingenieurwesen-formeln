# quanta-ingenieurwesen-formeln

**135 ingenieurwesen references**, maintained by [Quanta Study](https://quanta-study.de/), a product of **AM Creative Tech UG (haftungsbeschränkt)**. Version **1.0.0** describes the files in this repository; npm publication is a separate action. This update provides a GitHub dataset; npm publication is disabled with private:true.

## What can I use this for?

Look up compact formula records in a website, teaching tool or local script. Each record includes notation, subject and chapter metadata, education levels, short variable labels and units, bibliographic references and a canonical Quanta reference URL. Formula text is **German**; the developer documentation is English. No English formula overlay is included.

Read [formeln.json](./formeln.json) directly or use the zero-dependency CommonJS helpers and [TypeScript declarations](./index.d.ts). This is reference data, not a copy of the interactive learning platform.

## Use the GitHub checkout or JSON

```sh
git clone https://github.com/ammmcreativetech-dot/quanta-ingenieurwesen-formeln.git
cd quanta-ingenieurwesen-formeln
node -e "console.log(require('./').formeln.length)"
```

Verify the checkout's package version and [manifest](./manifest.json) when reproducibility matters. No npm installation command is required for this workflow.

```js
const {getFormelBySlug, getAbiturFormeln} = require('./');
const formula = getFormelBySlug('young-modul');
console.log({slug: formula.slug, latex: formula.latex, url: formula.url});
const abiturReferences = getAbiturFormeln();
const raw = require('./formeln.json');
```

Selected fields from that actual record:

```json
{
  "slug": "young-modul",
  "name": "Young’scher Modul",
  "latex": "E = \\frac{\\sigma}{\\varepsilon} = \\frac{F L_0}{A_0 \\Delta L}",
  "kategorie": "ingenieurwesen",
  "url": "https://quanta-study.de/tafelwerk/young-modul"
}
```

Explore [Young’scher Modul](https://quanta-study.de/tafelwerk/young-modul) in context, or browse the public [Quanta Tafelwerk](https://quanta-study.de/tafelwerk). The online explanations and learning features remain separate from this dataset.

## API

- `formeln` and `getAllFormeln()`: all records in this package.
- `getFormelBySlug(slug)`: one matching record, or `undefined`.
- `getFormelByKategorie(subject)`: exact subject filter.
- `getFormelByUnterkategorie(label)`: original short-label filter.
- `getFormelByKapitel(chapter)`: stable chapter-ID filter.
- `getFormelByBildungsniveau(level)`: education-level filter.
- `getAbiturFormeln()`: records whose original `abiturRelevant` flag is true. It does not assert permission to use a resource during an exam.

Every record and the category type in this package remain narrowed to `ingenieurwesen`. Historical core helpers keep their meanings; the subcategory helper, originally available in the subject packages, is also available in the core. Direct JSON access and CommonJS remain supported. Existing helper names in the four older subject packages are preserved.

## Compatibility

This is the first standalone version of this subject dataset. The compact field contract is documented in [schema.json](./schema.json). Scientific values are not silently truncated. References identify sources; their presence does not certify correctness or license the referenced works.

## Questions

### Does this include full articles or worked solutions?

No. It includes compact reference metadata and notation. Article text, descriptions, derivations, solutions, FAQs, calculator implementations and learning blueprints are excluded.

### Which language is the data in?

Formula records are German. English is used for documentation.

### Where can I go deeper?

Use a record's canonical `url` or the [Tafelwerk hub](https://quanta-study.de/tafelwerk) for online context. This repository offers reusable reference data; it makes no learning-gain, search-ranking or AI-citation promise.

## Provenance, citation and license

Source dataset revision: `99ae5619a30cd0a3e883ddd8da8c23f1199fa416`; public source: [Quanta Tafelwerk](https://quanta-study.de/tafelwerk). [manifest.json](./manifest.json) records schema, counts and SHA-256 checksums. [CITATION.cff](./CITATION.cff) supplies dataset attribution without inventing a DOI or release date.

The included dataset, small wrappers and repository files continue under **[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)**; see the full [LICENSE](./LICENSE) and [scope notice](./LICENSE-SCOPE.md). Attribute **Quanta Study — AM Creative Tech UG (haftungsbeschränkt)**, retain the license notice and indicate changes as required by the license. Earlier public CC BY 4.0 grants remain unchanged. The full application, online articles and other materials not included here are not licensed by this repository.

## Check locally

```sh
npm test
npm pack --dry-run --ignore-scripts
```

No dependency installation is needed. Publication is never triggered by an ordinary data push. This repository has no npm-publish workflow.
