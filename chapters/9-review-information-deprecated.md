# 13 Review information fields (deprecated)

The review information section is included for compatibility with SPDX 1.2, and is deprecated since SPDX 2.0. Any review information should use an Annotation (as described in Clause [12](./8-annotations.md)) with an annotation type of `REVIEW`.

Review information can be added after the initial SPDX file has been created. The set of fields are optional and multiple instances can be added. Once a Reviewer entry is added, the Review Date associated with the review is mandatory. The Created date should not be modified as a result of the addition of information regarding the conduct of a review. A Review Comments is optional.

Fields:

## 13.1 Reviewer field (deprecated) <a name="9.1"></a>

This field has been deprecated since SPDX 2.0.

**Description**

This field identifies the person, organization or tool that has reviewed the SPDX file. This field is optional and thus there is no requirement for any reviewer to add a set of review information to the file. This can be considered as an equivalent to “signed off” or “reviewed by.” Additional reviewers can be added after the original version of the SPDX file is created and be appended to the original file.

**Intent**

Here, as time progresses certain reviewers will begin to gain credibility as reliable. This field intends to make such information transparent. It may also be important for participants in the software supply chain to validate whether upstream providers have reviewed the SPDX file.

**Metadata**

The metadata for the reviewer field is shown in Table 76.

Table 76 — Metadata for the reviewer field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | Single line of text with the following keywords.<br><pre>"Person: person name" and optional "(email)"<br>"Organization: organization" and optional "(email)"<br>"Tool: tool identifier - version"</pre> |

**Examples**

EXAMPLE 1 Tag: `Reviewer:`

```text
Reviewer: Person: Jane Doe ()
```

EXAMPLE 2 RDF: Property `spdx:reviewer` in class `spdx:Review`

```text
<Review>
    <reviewer> Person: Jane Doe () </reviewer>
</Review>
```

## 13.2 Review date field (deprecated) <a name="9.2"></a>

This field has been deprecated since SPDX 2.0.

**Description**

Identify when the review was done. This shall be specified according to the combined date and time in the UTC format, as specified in the ISO 8601 standard.

**Intent**

Here, the `ReviewDate` can serve as a verification as to when the actual review was done.

**Metadata**

The metadata for the review date field is shown in Table 77.

Table 77 — Metadata for the review date field

| Attribute | Value |
| --------- | ----- |
| Required | Conditional |
| Cardinality | 0..1 conditional (Mandatory, one), if there is a Reviewer. |
| Format | `YYYY-MM-DDThh:mm:ssZ`<br>where:<br><ul><li>`YYYY` is year</li><li>`MM` is month with leading zero</li><li>`DD` is day with leading zero</li><li>`T` is delimiter for time</li><li>`hh` is hours with leading zero in 24 hour time</li><li>`mm` is minutes with leading zero</li><li>`ss` is seconds with leading zero</li><li>`Z` is universal time indicator</li></ul> |

**Examples**

EXAMPLE 1 Tag: `ReviewDate:`

```text
ReviewDate: 2010-01-29T18:30:22Z
```

EXAMPLE 2 RDF: Property `spdx:reviewDate` in class `spdx:Review`

```text
<Review>
    <reviewDate> 2010-01-29T18:30:22Z </reviewDate>
</Review>
```

## 13.3 Review comment field (deprecated) <a name="9.3"></a>

This field is deprecated since SPDX 2.0.

**Description**

This optional free form text field permits the reviewer to provide commentary on the analysis.

**Intent**

This allows the reviewer to provide independent assessment and note any points where there is disagreement with the analysis.

**Metadata**

The metadata for the review comment field is shown in Table 78.

Table 78 — Metadata for the review comment field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | Free form text that may span multiple lines. |

**Examples**

EXAMPLE 1 Tag: `ReviewComment:`

In `tag:value` format multiple lines are delimited by `<text> .. </text>`.

```text
ReviewComment: <text>All of the licenses seen in the file, are matching what was seen during manual inspection.
There are some terms that can influence the concluded license, and some alternatives may be possible,
but the concluded license is one of the options.</text>
```

EXAMPLE 2 RDF: Property `rdfs:comment` in class `spdx:Review`

```text
<Review>
    <rdfs:comment>All of the licenses seen in the file, are matching what was seen during manual inspection.
    There are some terms that can influence the concluded license, and some alternatives may be possible,
    but the concluded license is one of the options.</rdfs:comment>
</Review>
```
