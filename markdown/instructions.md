[<img src="https://github.com/openvar/VV_databases/blob/markdown/markdown/static/VV_logo.png?raw=true" width="20%" />](https://variantvalidator.org/)

# VariantValidator Batch Tool Help

Using the VariantValidator Batch Tool to validate variant descriptions

## The basic steps:

[VariantValidator](https://variantvalidator.org/) is a web-based tool
that allows the checking of human genome sequence variant descriptions
for compliance with the HGVS Variant Nomenclature. Variants may be
checked individually or multiple variant descriptions may be checked
simultaneously by submitting them to the [Batch
Validator](https://variantvalidator.org/service/validate/batch/).

Variant descriptions are pasted into the Input Variant Descriptions data
entry box with one variant description per line. Instructions are provided
on-screen. Validation can be limited to a particular gene or genes. This
is particularly useful if you have a long list of variants that are
described in the context of genome coordinates, but only those that fall
into a particular gene or genes might be of interest. HGNC gene symbols are
used to impose gene search limits and the input is not case-sensitive.
The results are returned to you by email, so you must enter a valid
email address. 

Finally, you must select a genome build *i.e.*
- GRCh38 (hg38, build38)
- GRCh37 (hg19, build19)

to allow the validation of variant descriptions, such as

- 17-50198002-C-A
- chr17:50198002C\>A

where the appropriate genome
build cannot be deduced from the variant description itself. Needless to say,
it's not possible to simultaneously submit a mix of variant descriptions
from both genome builds.

## Formatting the data for validation

The ideal method to prepare your data is to use a plain text editor. Use of a word processor
is not recommended because of the potential to carry over non-valid
characters from your list of variant descriptions into the input box.
VariantValidator has been designed to strip out invalid characters but
it is better to avoid them being there in the first place. Copying
variant descriptions directly from journal articles and from web pages
can be equally problematic.

**Note:** It is vitally important that there be no trailing "invisible"
characters immediately after a variant
description. The presence of such characters can result in the
submission of a blank variant description which will return a "Variant
description is not in an accepted format" warning in the batch validator
report output. We are aware of this problem and blank spaces and tabs
are automatically stripped out of the submitted variant data. However, 
there are many other "invisible" characters that might cause validation problems.

A short list of valid variant descriptions might look like this:

```text
NM_000088.4:c.589G>T
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

The following variant ten descriptions are invalid and are each expected to
return an error message:

 ```text
NM_000088.4:c.589C>T
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

****

## Customising the ouput file

The batch tool allows you to customise the information that is returned
in the output file. By default, all computed information is returned, but
you may use the check-boxes to select or exclude specific information types.

Customising the output file may be of use when using the batch tool for
specific tasks where some outputs might not be relevant.

****

## What happens next?

When you press the submit button, you will immediately receive
confirmation on screen that your job has been submitted. This on-screen
confirmation will also include a Job ID which will look something like
Job ID: 17e4fa8b-e4c3-4d1f-bfab-79c6366357e1. In addition,
you will receive a confirmation by email which includes a Request ID and
the date and time at which the request was submitted. The time taken for
the return of your results will depend on the number of other jobs ahead
of you in the queue and the number of variant descriptions to be
validated in your job. The email confirmation explains this and provides
contact information if you have any queries. When your job is complete,
you will receive a second email containing a link to download your results
from our server. The download is initiated by clicking on the link in
the email. Results are stored on the server only for seven days and are then deleted.

****

## What have I downloaded?

When you click on the link, the results are returned to you as plain
text that you will need to save on your computer. Forcing you to save
the file is deliberate as the results will only be stored on the server
for seven days. The data are in what is known as "tab-delimited"
format. It is human readable, but is best opened in a spreadsheet
program such as Microsoft Excel or LibreOffice Calc. Just accept the
default actions for which you will be prompted by Excel or Calc.

Once your data have been imported into your spreadsheet program of
choice, you can customise the view by adjusting the widths of the
columns in the table view. Excel provides an "AutoFit Column Width"
funtion to help with this. No other adjustments should be necessary, and
you should now be able to easily read the results. Not all of the
columns will necessarily be of value to you.

Finally, and importantly, once you have imported your results into a
spreadsheet, be sure to save the spreadsheet in its native Excel or Calc
format. If you forget, you will have to repeat the import process.

The key first task is to check for any errors or warnings in column B
(Warnings) which reports both errors and warnings (Including
any automatic corrections which VariantValidator may have performed).
Errors indicate that a variant description has failed to validate
correctly, but warnings are intended to convey information. The meaning
of the various errors and warnings is explained more fully below. If you
encounter any errors, you should fix them and resubmit corrected
descriptions to the Batch Validator. Please resubmit only those
descriptions that need to actually be validated. Resist the temptation
to resubmit the variants that have already passed validation.


Example output files, derived form the example data above, can be
accessed as
[valid_variant_test_results.txt](https://raw.githubusercontent.com/openvar/VV_databases/markdown/markdown/static/valid_variant_test_results.txt)
and
[invalid_variant_test_results.txt](https://raw.githubusercontent.com/openvar/VV_databases/markdown/markdown/static/invalid_variant_test_results.txt)


****

## Metadata

VariantValidator will automatically add meta data to the second line of
your results file. The data will provide information such as the software
versions, the database versions, and which output options you selecetd. We
recommend that you retain these data as it will help us to resolve any
issues that you may encounter in the future.



****

## Using the batch tool to validate varaints for submission to journals

Some biomedical journals now require authors to validate variant descriptions
that will be included in submitted manuscripts. VariantValidator has been adopted
as a recognised validation tool by journals for this purpose.

You must include the output file generated by the VariantValidator Batch tool
alongside the manuscript when submitting to a journal that has adopted a policy
of variant validation.

**Errors in variant descriptions that are identified by VaraintValidator (including
 those that are automatically corrected by VariantValidator) MUST be
corrected in manuscripts prior to submission. Journals will not make corrections on
your behalf. Be certain that the output file that is submitted to the journal
correposnds to the corrected variant descriptions.**

Some journals might specify which specific information should be in the output
file. If there is any doubt about the information that is required, ensure that
you select all information in the output file (see above).

When submitting intronic variants to journals, you must include either a
Genomic context description or a RefSeqGene context description (if a RefSeqGene
reference sequence exists that fully encompasses the variant).

****

## Error warnings that need to be corrected:
VariantValidator is designed to detect errors, but not all errors can be
corrected automatically. The following errors require correction by the user:

-   **Variant reference (C) does not agree with reference sequence (G):**\
     The variant decription, e.g. c.472C>T, specifies that the reference
     base is a C, whereas the base at position 472 of the reference sequence is
    actually a G. The user must correct the description and resubmit it.

-   **Using a transcript reference sequence to specify a variant position that lies
     outside of the reference sequence is not HGVS-compliant. Instead re-submit
    NC_000006.12:g.32038297C>T:**\
    The HGVS nomenclature does not allow variant descriptions in which the sequence alteration lies outside of the reference sequence, either wholly or in part. In this example, the sequence alteration has been determined in the chromosomal context relative to the
    transcript and the user is directed to submit NC_000006.12:g.32038297C>T for validation
    instead.

-   **The specified coordinate is outside the boundaries of reference sequence NC_000017.11:**\
    This error message indicates that the variant descrption specifies a location that lies
    outside of the the example reference sequence (NC\_000017.11) which represnets chromosome
    17. The user must correct the description and resubmit it.

-   **HGVS variant nomenclature does not allow the use of a gene symbol (COL5A1) in place of a    valid reference sequence: Re-submit COL5A1:c.5071A>T and specify transcripts from the following: select_transcripts=NM_000093.4|NM_001278074.1|NM_000093.3:**\
    A gene symbol (e.g. COL5A1) cannot be used in place of a valid reference sequence to
    validate a variant description. In this example, three valid transcript reference
    sequences are suggested. The user must select a valid transcript and resubmit the
    validation task. 

-   **Uncertain positions are not currently supported:**\
    It's debatable whether this is a true error message. However, it indicates that a
    variant description containing an undefined base location (e.g. c.1576+1_?del) has
    been submitted. It is simply not possible to validate varaint descriptions that
    contain uncertain (undefined) positions.

-   **Failed to fetch NC_000071.10 from SeqRepo (/local/seqrepo/VV_SR_2021_2/master) (Alias NC_000071.10 (namespace: None)):**\
    The submitted variant description in this example includes a reference sequence (NC_000071.10) that is not present in SeqRepo which is the sequence respository used by VariantValidator to store reference sequences. In this example, the error is caused by a typo: NC_000071.10 should be NC_000017.10 as the former is invalid because no such sequence accession/version exists. An error of this type might also be generated if a varaint is described in the context of a valid reference sequence that happens not to be present in SeqRepo. That might occur for legacy transcript reference sequences that map to neither GRCh37 nor GRCh38, or have been formally retired by NCBI.

****

## Warnings that are not errors, but are provided as guidance:

Some warning messages that are produced by the batch validator are not
really errors, but are designed to provide useful guidance. Examples (in no
particular order) of such warnings include:

-   **A more recent version of the selected reference sequence
    NM_000022.2 is available (NM_000022.3):**\
     This is a specific example for RefSeq record NM\_000022. Although
    it is considered best-practice to report variants in the context of
    the most up-to-date reference sequence, the HGVS guidelines do not
    require that this be done.
    Hence, it is up to the user, or perhaps the policy of journals in
    which they hope to publish results, whether they choose to use the
    updated reference sequuence.
    
-   **No transcript definition for (tx_ac=NM_003919.3):**\
    This is a specific example for RefSeq record NM\_003919.3. The transcipts
    against which variants may be validated need to be present in the
    current version of the VariantValidator Transcript Archive (VVTA). We aim
    to update VVTA on a regular basis, but there may be new transcript versions
    that are not yet included.

-   **No transcripts found that fully overlap the described variation in
    the genomic sequence:**\
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

-   **Removing redundant reference bases from variant description:**\
     This warning is displayed when a deletion variant description includes
     the actual deleted bases, e.g. NM\_000088.4:c.1_3delATG. The three
     deleted bases are fully defined in the context of their positions in the
     reference sequence and are hence redundant. VariantValidator automatically
     removes redundant bases from variant descriptions.

-   **NM_000088.3:c.589GG>CT automapped to NM_000088.3:c.589_590delGGinsCT:**\
    This warning indicates that the example varaint description is not HGVS
    compliant and that VariantValidator has corrected the description.

-   **LRG_1:g.8638G>T automapped to NG_007400.1:g.8638G>T:**\
    An LRG record comprises a gene sequence and one or more corresponding
    transcript sequences. The gene and transcript sequences uniquely map to
    RefSeqGene and RefSeq records respectively. In this example, the LRG gene
    sequence variant description (LRG_1:g.8638G>T) has been automapped to its
    corresponding RefSeqGene variant description (NG_007400.1:g.8638G>T).

-   **LRG_1t1:c.589G>T automapped to NM_000088.3:c.589G>T:**\
    An LRG record comprises a gene sequence and one or more corresponding
    transcript sequences. The gene and transcript sequences uniquely map to
    RefSeqGene and RefSeq records respectively. In this example, the LRG transcript
    t1 sequence variant description (LRG_1t1:c.589G>T) has been automapped to its
    corresponding RefSeq transcript variant description (NM_000088.3:c.589G>T).    

****

## Getting help

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

****

## How to cite VariantValidator

If you use VariantValidator in your research, we would be grateful if
you would cite the publication that describes it:

VariantValidator: Accurate validation, mapping and formatting of
sequence variation descriptions.\
 Freeman PJ, Hart RK, Gretton LJ, Brookes AJ, Dalgleish R. (2018) *Human
Mutation* 39:61-68.
[https://doi.org/10.1002/humu.23348](https://doi.org/10.1002/humu.23348)\
This publication is Open Access.

****

## Document Version 1.0.1
Raymond Dalgleish, 19 August 2021

Copyright © 2021 VariantValidator Contributors


***
[<img src="https://github.com/openvar/VV_databases/blob/markdown/markdown/static/Manchester_logo.png?raw=true" width="30%" />](http://https://www.manchester.ac.uk/)

<br>

[<img src="https://github.com/openvar/VV_databases/blob/markdown/markdown/static/uniofleicesterlogo.png?raw=true" width="30%" />](http://le.ac.uk)
