[<img src="https://github.com/openvar/VV_databases/blob/markdown/markdown/static/VV_logo.png?raw=true" width="20%" />](https://variantvalidator.org/)

# VariantValidator Batch Tool Help

Using the VariantValidator Batch Tool to validate variant descriptions

### The basic steps:

[VariantValidator](https://variantvalidator.org/) is a web-based tool
that allows the checking of human genome sequence variant descriptions
for compliance with the HGVS Variant Nomenclature. Variants can be
checked individually or multiple variant descriptions can be checked
simultaneously by submitting them to the [Batch
Validator](https://variantvalidator.org/service/validate/batch/).

Variant descriptions are pasted into the Input Variant Descriptions data
entry box with one description per line. Instructions are provided
on-screen. Validation can be limited to a particular gene or genes. This
is particularly useful if you have a long list of variants that are
expressed in the context of genome coordinates, but only those that fall
into a particular gene or genes are of interest. HGNC gene symbols are
used to impose gene search limits and the input is not case-sensitive.
The results are returned to you by email, so you must enter a valid
email address. 

Finally, you must select a genome build *i.e.*
- GRCh38
- GRCh37

to allow the validation of variant descriptions, such as

- 17-50198002-C-A
- chr17:50198002C\>A, where the appropriate genome
build cannot be deduced from the description itself. Needless to say,
it's not possible to simultaneously submit a mix of variant descriptions
from both genome builds.

### Formatting the data for validation

The ideal method is to use a plain text editor. Use of a word processor
is not recommended because of the potential to carry over non-valid
characters from your list of variant descriptions into the input box.
VariantValidator has been designed to strip out invalid characters but
it is better to avoid them being there in the first place. Copying
variant descriptions directly from journal articles and from computer
screens can be equally problematic.

**Note:** It is vitally important that there be no trailing "invisible"
characters, such as spaces or tabs, immediately after a variant
description. The presence of such characters can result in the
submission of a blank variant description which will return a "Variant
description is not in an accepted format" warning at the end of the
batch validator output. We are aware of this problem and will apply a
software patch as soon as possible to handle the issue.

A short list of valid variant descriptions might look like this:

```text
NM_000088.3:c.589G>T
NC_000017.10:g.48275363C>A
NG_007400.1:g.8638G>T
LRG_1:g.8638G>T
LRG_1t1:c.589G>T
17-50198002-C-A
chr17:50198002C>A
```

Note that the final two variant descriptions are in the context of
GRCh38. It's also worth noting that each of these seven variant
descriptions is valid and should return no error messages.

The following variant descriptions are invalid and are each expected to
return an error message:

 ```text
NM_000088.3:c.589C>T
NC_000071.10:g.48275363C>A
NG_007400.2:g.8638G>T
LRG_1:g.8638G>N
LRG_1t3:c.589G>T
17-50198002-G-A
chr17:550198002C>A
COL5A1:c.5071A>T
NM_000088.3:c.589GG>CT
NM_000500.7:c.-107-19C>T
```

Plain text files containing these variant descriptions can accessed
as
[valid_variant_test_set.txt](https://raw.githubusercontent.com/openvar/VV_databases/markdown/markdown/static/valid_variant_test_set.txt)
and
[invalid_variant_test_set.txt](https://raw.githubusercontent.com/openvar/VV_databases/markdown/markdown/static/invalid_variant_test_set.txt)

### What happens next?

When you press the submit button, you will immediately receive
confirmation on screen that your job has been submitted. In addition,
you will receive a confirmation by email which includes a Request ID and
the date and time at which the request was submitted. The time taken for
the return of your results will depend on the number of other jobs ahead
of you in the queue and the number of variant description to be
validated in your job. The email confirmation explains this and provides
contact information if you have any queries. When your job is complete,
you will receive another email explaining how to download your results
from our server. The download is initiated by clicking on the link in
the email. Results are stored only for seven days and are then deleted.

### What have I downloaded?

When you click on the link, the results are returned to you as plain
text that you will need to save on your computer. Forcing you to save
the file is deliberate as the results will not be stored permanently
beyond seven days. The data are in what is known as tab-delimited
format. It is human readable, but is best opened in a spreadsheet
program such as Microsoft Excel or OpenOffice Calc. Just accept the
default actions for which you will be prompted by Excel or Calc.

Once your data have been imported into your spreadsheet program of
choice, you can customise the view by adjusting the widths of the
columns in the table view. No other adjustments should be necessary, and
you should now be able to easily read the results. Not all of the
columns will necessarily be of value to you.

The key first task is to check for any errors or warnings in column B
(validation\_warnings) which reports both errors and warnings (Including
any automatic corrections which VariantValidator may have performed).
Errors indicate that a variant description has failed to validate
correctly, but warnings are intended to convey information. If you
encounter any errors, you should fix them and resubmit corrected
descriptions to the Batch Validator. Please submit only those
descriptions that need to actually be validated. Resist the temptation
to resubmit the variants that have already passed validation.

You must use the outputs provided by VariantValidator for submission to
journals, not the variant descriptions that you submitted

When submitting intronic variants to journals, you must use either a
chromosomal context or RefSeqGene context intronic variant description
as provided by the tool

Two common warnings that you might see relate to Locus Reference Genomic
(LRG) and NCBI RefSeq transcript and gene reference sequences. The
validator automatically projects variants onto LRG reference sequences
(gene and transcript(s)) if an LRG exists for the gene to which the
variant maps. A warning will be generated if that LRG is currently
flagged as "pending". LRG-based variant descriptions should only be used
for LRGs that are finalised.

If you have submitted a variant description for validation using RefSeq
transcript or gene that is not the most recent version, this will
trigger a warning. It's not an error. The warning is to simply alert you
that a newer version of the transcript or gene sequence record exists
and you may wish to resubmit the variant description in the context of
that newer version. If your variant description validates correctly in
the context of an older version of a reference sequence, that is okay.
The HGVS variant nomenclature guidelines do not require use of the most
recent version.

Example output files, derived form the example data above, can be
accessed as
[valid_variant_test_results.txt](https://raw.githubusercontent.com/openvar/VV_databases/markdown/markdown/static/valid_variant_test_results.txt)
and
[invalid_variant_test_results.txt](https://raw.githubusercontent.com/openvar/VV_databases/markdown/markdown/static/invalid_variant_test_results.txt)

Finally, and importantly, once you have imported your results into a
spreadsheet, be sure to save the spreadsheet in its native Excel or Calc
format. If you forget, you will have to repeat the import process.

### Getting help

VariantValidator has been developed to meet the many needs of our users.
We understand that many users find it difficult to write variant
descriptions for submission to VariantValidator, and we realise that
many aspects of the HGVS nomenclature are difficult to comprehend (for
expert and novice users alike). We encourage our users to contact us if
they are having difficulty with reporting their sequence variants by
filling in a [basic web form](https://variantvalidator.org/help/contact/). We will endeavour to
contact you as soon as we can to provide you with the guidance that you
require. Users can also report processing errors and make feature
requests by contacting us on
[GitHub](https://github.com/openvar/variantValidator/issues).

### Metadata

VariantValidator will automatically add meta data to the top and tail of
your file. The data will provide information such as the software
version and database versions. We recommend that you retain these data
as it will help us to resolve any issues that you may encounter in the
future.

### Warnings that are not errors:

Some warning messages that are produced by the batch validator are not
errors, but are designed to provide useful guidance. Examples (in no
particular order) of such warnings include:

-   **A more recent version of the selected reference sequence
    NM_000022.2 is available (NM_000022.3):**
     This is a specific example for RefSeq record NM\_000022. Although
    it is considered best-practice to report variants in the context of
    the most up-to-date reference sequence, HGVS does not demand this.
    Hence, it is up to the user, or perhaps the policy of journals in
    which they hope to publish results, whether they choose to use the
    updated description.
    
-   **No transcripts found that fully overlap the described variation in
    the genomic sequence:**
     Some genome sequence variants will lie outside of genes and will
    not project onto (align with) a gene transcript. Some variants might
    project only partially onto a transcript. In both instances, this
    warning will be generated.
    
-   **The current status of LRG\_XYZ is pending therefore changes may be
    made to the LRG reference sequence:**\
     Locus Reference Genomic (LRG) reference sequences may be made
    available for use prior to the content being fully approved and LRG
    record being designated as being “Public”. Any LRG that is
    designated as being “Pending” is not stable and may be subject to
    change.
    
-   **This coding sequence variant description spans at least one
    intron; use of the corresponding genomic sequence variant
    descriptions may be invalid:**\
     Sequence variants, such as deletions, that have been discovered by
    RNA sequencing might appear to span at least one intron. However,
    such a deletion might not be due to a single mutational event and
    attempts to project the deletion from a transcript to the genome
    might be invalid.
    
-   **Protein level variant descriptions are not fully supported due to
    redundancy in the genetic code:**\
     VariantValidator can verify the syntax and the reference amino
    acid(s) specified in a protein-level variant description. However,
    it is impossible to project such a variant to a transcript or to the
    genome because of redundancy in the genetic code.
    
-   **RefSeqGene record not available:**\
     Only some genes have an NCBI RefSeqGene record. This warning simply
    indicates that no RefSeqGene record exists for the gene in which the
    variant that is being validated resides.

### How to cite VariantValidator

If you use VariantValidator in your research, we would be grateful if
you would cite the publication that describes it:

VariantValidator: Accurate validation, mapping and formatting of
sequence variation descriptions.\
 Freeman PJ, Hart RK, Gretton LJ, Brookes AJ, Dalgleish R. (2018) *Human
Mutation* 39:61-68.
[https://doi.org/10.1002/humu.23348](https://doi.org/10.1002/humu.23348)


### Document Version 0.5
Raymond Dalgleish, 4 June 2020

Copyright © 2020 VariantValidator Contributors


***
[<img src="https://github.com/openvar/VV_databases/blob/markdown/markdown/static/Manchester_logo.png?raw=true" width="30%" />](http://https://www.manchester.ac.uk/)

<br>

[<img src="https://github.com/openvar/VV_databases/blob/markdown/markdown/static/uniofleicesterlogo.png?raw=true" width="30%" />](http://le.ac.uk)
