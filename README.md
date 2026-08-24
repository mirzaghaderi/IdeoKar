# IdeoKar2

A Java tool for extracting chromosomal/karyotypic
parameters from metaphase chromosome-spread images and building ideograms from chromosomes images or genomic data,
for single species, multi-species or allopolyploids.

## System Requirements

IdeoKar2 can be run in two ways:
 
1. Installing on windows using msi installation file (Operating System: Windows only). Download IdeoKar2_win.msi and extract. Instal as a common windows installer then double-click IdeoKar2 icon to launch IdeoKar.
 
2. Compiled JAR file which works on Windows, Linux, or macOS provided that Java Runtime Environment (JRE) or Java Development Kit (JDK) is installed. Check Java Installation. Open Command Prompt (CMD) or a terminal and run:
 
```
java -version
```
 
If Java is installed, you should see the installed Java version, for example:
 
```
openjdk version "17.x.x"
```
 
Run IdeoKar
Place IdeoKar2.jar file in a convenient folder. Open CMD and navigate to that folder:
 
```
cd C:\Path\To\IdeoKar
 
```
 
Then run:
 
```
java -jar IdeoKar2.jar
```


![IdeoKar2 – three-window layout](IdeoKar2.jpg)

*Figure 1 – The main working windows of IdeoKar2. Chromosomes may be traced manually or generated using the auto-trace option. Automatically generated traces can subsequently be inspected and manually adjusted, for example by retracing individual chromosomes, repositioning centromeres, and correcting chromosome names or assignments.*




<figure>
    <img src="ideogram1.jpg" style="width: 50%;" alt="Figure 2" />
  <figcaption aria-hidden="true">
    Figure 2: A sample ideogram output of IdeoKar2. The legend and chromosome labels can be edited by double-clicking them. The legend can also be moved, hidden, or removed according to the user's needs.
  </figcaption>
</figure>

<p><br></p>



<figure>
    <img src="windows4.jpg" style="width: 100%;" alt="Figure 3" />
  <figcaption aria-hidden="true">
    Figure 3: Four-window layout of IdeoKar2 showing the integrated workflow for chromosome analysis. The Core window is used to open metaphase chromosome-spread images, define scale, trace chromosomes, and inspect or manually adjust chromosome traces. The Parameters window presents calculated karyotype-level, chromosomal, and raw tracing data. The Ideogram window displays the final chromosome ideogram with genome/sub-genome rows, chromosome labels, scale information, and an editable legend. The Karyogram window provides an organized view of the traced chromosomes for visual quality control and manual adjustment of chromosome organization. A chromosome selected in the Karyogram can be linked back to its corresponding source-image trace, which is highlighted in the Core window to facilitate direct inspection and correction. Together, these windows support a workflow from automatic or manual tracing, through inspection and adjustment, to calculation of chromosomal parameters and generation of the final ideogram.
  </figcaption>
</figure>

<p><br></p>


## IdeoKar2 main windows

1. **Core window**: contains the main karyotyping toolbar and a tabbed area with one
   tab per opened image. This is the main workspace for chromosome spread viewing,
   chromosome tracing, scale definition, and manual inspection of traces.

2. **karyotyping parameters window**: opens or refreshes when you click `Run Ideogram`. It contains
   three tabs:
   - **Karyotype parameters**: per-genome or per-sub-genome aggregates.
   - **Chromosomal parameters**: per-chromosome results.
   - **Raw data**: traced coordinates and landmark data.

3. **Ideogram window** — opens after `Run Ideogram`. It displays ideogram and contains adjusting controllers. 

4. **Karyogram window** — opens by `Run Ideogram` and provides an organized visual view of the traced
   chromosomes for quality control and manual
   inspection of chromosome assignments. Chromosomes can be reviewed as a
   group, and the Karyogram can be used to identify chromosomes that require
   further inspection or adjustment in their original source images. Clicking
   a chromosome in the Karyogram selects the corresponding chromosome trace
   in its source image and highlights it, making it easier to move directly
   from the karyotype-level view to detailed inspection of the original trace.

## Auto-Tracing and Manual Inspection/Adjustment

IdeoKar2 supports both **automatic chromosome tracing (auto-trace)** and
**manual chromosome tracing**. Auto-tracing can substantially speed up the
initial extraction of chromosome traces from suitable metaphase spread images,
while manual tracing remains available when a chromosome is not correctly
traced. Automatic tracing should be treated as an initial tracing step rather than as
a substitute for visual quality control. Depending on image quality and chromosome
overlap, an automatically generated trace may require correction before the chromosome
is used for quantitative analysis.

## A recommended workflow

1. Open one or more chromosome spread images. Each opens in its own tab.
2. click the button, then click two points of known distance (scale bar) in the active image. A popup asks for that distance in micrometers.
3. Optional image processing: This includes Crop, Remove background, knife tools described above.
4. Trace chromosomes: use auto-trace when appropriate or trace manually.
   For manual tracing, left-click to lay down connected segments along the
   chromosome. At landmark points, either right-click for a context menu or
   use the following hotkeys:
   - `Ctrl+C` — Centromere.
   - `Ctrl+R` — Red segment start/end (press once to start and again to close).
   - `Ctrl+O` — Orange segment start/end.
   - `Ctrl+G` — Green segment start/end.
   - `Ctrl+B` — Black segment (heterochromatin) start/end.
   - `Ctrl+F` — Finish chromosome (opens a naming dialog).
5. Inspect and adjust traces: review automatically generated or manually
   traced chromosomes in the Core window. Retrace individual chromosomes if required,
   reposition centromeres, and correct chromosome names or assignments when
   needed. Use `Ctrl+Z` to undo a segment or use `Undo Chromosome`.
6. Select and delete a chromosome: clicking a traced chromosome highlights
   it in yellow. Pressing `Delete` removes the selected chromosome.
7. 'Run Karyogram' opens a window that copies every finished traced
  chromosome out of its source image as a real cutout and gives each genome/sub-genome
  its own row. Within a row, homologs (same number, whether traced in
  the same image or different images) are grouped side by side, ordered left to right from largest to smallest.
Drag a chromosome onto another group (in the same row or a
  different genome's row) to reassign it there, or drag it within
  its own group to reorder it. Each time you do this, every row is renumbered from 1 in size order and the new numbers are written back to this tracing window
8. Run ideogram: computes parameters and (re)builds the ideogram.
9. Save Table / Save Ideogram: export results.
10. Zoom — hold `Ctrl` and scroll the mouse wheel over the active image to
    zoom in or out. Zooming is centered on the exact location under the mouse
    pointer, allowing detailed inspection of a specific chromosome or image
    region.

## Computed parameters

Per chromosome: short arm (S), long arm (L), total length (TCL = S+L), arm
ratio (L/S), centromeric index (S/TCL×100), relative length (chromosome's
share of its genome's total complement length), Levan-type classification
(m/sm/st/a/t), heterochromatin length and %, and 45S/5S rDNA site counts.

Per genome/sub-genome: chromosome count, total complement length, mean
chromosome length, summed arm lengths, mean arm ratio, mean centromeric
index, CVCL and CVCI (coefficients of variation of length and centromeric
index — inter-/intra-chromosomal asymmetry measures), the Romero-Zarco
(1986) A1/A2 asymmetry indices, and a karyotype formula (e.g. `6m + 2sm`).


## Save Project 

Save Project saves the complete project into the first image folder 
selected/used by the user. The project file stores the necessary 
relative image paths, so the project remains portable with its image folder.
Open Project can reopen the project later and restore the previous 
activities/settings. Existing tracing data, chromosome information, labels, 
colored segments, scaling, and other project settings will be preserved.


## Excel output

The Excel workbook contains:
1. Chromosomal parameters — homologous-group means and SE values.
2. Raw data — original traced pixel coordinates and landmarks.
3. Karyotype parameters — karyotype-level indices and Stebbins class.


## Chromosome banding

When one colored and one or more uncolored chromosomes with the same 
chromosome number are traced, the mean chromosome arm sizes are calculated 
from all traced homologs, while colored segments are mapped onto the mean chromosome 
rather than using the original traced chromosome's absolute arm length. 
Segment positions are scaled independently for the short and long arms so that
if the colored chromosome's short arm is shorter than the mean, the colored 
segment is expanded proportionally. If it is longer, the segment is proportionally 
shrunk. This enables simultaneous karyotyping and banding image preparation.

## Movable and Editable Legend

IdeoKar includes a customizable legend for chromosome ideograms. The legend automatically displays only the colors currently used for chromosome features and can be shown or hidden using the Show Legend controller. Users can drag the legend to reposition it on the image and edit individual legend descriptions. The legend can also be selected and deleted using the Delete key, and restored at any time by enabling Show Legend. The legend is included in exported image and PDF outputs.


## Abbreviations

| Parameter | Formula / Definition | Reference |
|-----------|----------------------|-----------|
| L | Mean length of long arm | |
| S | Mean length of short arm | |
| CL | Chromosome length = L + S | |
| AR | Arm Ratio = L/S | |
| r-value | S/L | |
| RL% | Relative length of chromosome = (CL / Sum(CL)) * 100 | |
| CI | Centromeric index = S / CL | |
| Chromosome type | Defined Terms in Table 2 of the KaryoMeasure manual | Levan et al., 1964 |
| F% | Form percentage of chromosome = (S / Sum(CL)) * 100 | |
| x | mean | |
| n | haploid chromosome number of an individual or a taxon | |
| s | standard deviation | |
| SE | standard error | |
| HCL | Total chromosome length of the haploid complement = Sum(CL) | |
| TF% | Total form percentage = (Sum(S) / Sum(CL)) * 100 | Huziwara, 1962 |
| Stebbins | Stebbins asymmetry index A–C, 1-4 (Table 3 of KaryoMeasure manual) | Stebbins, 1971 |
| AsK% | Arano index of karyotype asymmetry = (Sum(L) / Sum(CL)) * 100 | Arano, 1963 |
| A1 | Intrachromosomal asymmetry index = 1 - [Sum(Si / Li) / n] | Romero-Zarco, 1986 |
| A2 | Interchromosomal asymmetry index = sCL / xCL | Romero-Zarco, 1986 |
| S% | Symmetry index = (CL<sub>min</sub> / CL<sub>max</sub>) * 100 | |
| Xci | Mean centromeric index = Sum(CI) / n | |
| A | Degree of karyotype asymmetry = Sum((Li - Si) / (Li + Si)) / n | Watanabe et al., 1999 |
| Xca | Mean Centromeric Asymmetry = A * 100 | |
| CVcl | Coefficient of variation of chromosome length = (sCL / xCL) * 100 = A2 * 100 | Paszko, 2006 |
| Cvci | Coefficient of variation of centromeric index = (sCI / xCI) * 100 | Paszko, 2006 |
| AI | Asymmetry Index = (CVCL * CVCI) / 100 | Paszko, 2006 |



# Plugins

IdeoKar2 includes two built-in plugins that provide alternative ways to
construct an ideogram without manually tracing chromosomes in a
metaphase image. Both plugins use the same IdeoKar ideogram rendering
and parameter-calculation framework, so their generated ideograms can be
styled and exported through the normal Ideogram window.

## Dating Data plugin

The Dating Data plugin builds an ideogram directly from measured
chromosome dimensions. It is useful when chromosome measurements are
already available and an image-tracing workflow is unnecessary.
Open the plugin from the IdeoKar plugin menu. The main table contains:
Genome, Number, Short arm (µm), Long arm (µm), and Bands.


#### Adding bands

Select a chromosome and use **Add Band** to add a colored segment. Each
band is defined by Arm (Short arm or Long arm), Start (µm from centromere) (starting position measured from
    the centromere toward the arm tip), End (µm from centromere) (ending position measured from the
    centromere, and Color (Red, Orange, Green, or Black).
Chromosomes with the same Genome label are displayed together as one
ideogram row. If the Genome field is blank, the chromosomes are placed
in a single row.
Chromosomes having the same Genome + Number are treated as replicate
measurements of the same homologous chromosome group. Their measurements
are averaged in the same way that replicated chromosome measurements are
handled elsewhere in IdeoKar.

#### Importing and saving Dating Data

The plugin provides Load Example (loads a built-in example dataset), 
Load CSV... (imports chromosome and band measurements from a
    spreadsheet-friendly CSV file, Save CSV... (saves the current chromosome and band data as
    CSV), Load Project (imports finished,
    centromere-marked chromosomes and their colored segments directly
    from an IdeoKar project).

When importing an IdeoKar project, chromosomes without a marked
centromere are skipped because the plugin needs the centromere to
determine which arm contains each colored segment.
Click Generate Ideogram** after entering and checking the data. The
plugin converts the measurements into the same chromosome representation
used by the main IdeoKar application and opens the standard Ideogram
window. 
Save Table (.xlsx) exports the calculated numerical parameters after
an ideogram has been generated.


## Genomic Ideogram plugin

The Genomic Ideogram plugin constructs an ideogram directly from
genomic sequence data. It uses a FASTA file or a simple 3-column chromosome length table to obtain
chromosome sequences or lengths and can optionally use a GFF3
annotation file to obtain features information. If the genome FASTA sequence is loaded instead of the 3-column chromosome length table, it can also search the
genomic sequences for approximate repeat copies and display the
resulting repeat arrays as colored chromosome bands.



<figure>
    <img src="Figure 4.jpg" style="width: 100%;" alt="Figure 2" />
  <figcaption aria-hidden="true">
    Figure 4: Human chromosome ideogram generated using the Genomic Ideogram plugin of the IdeoKar2 tool, showing telomeric sequence, gene-density, and long non-coding RNA (lncRNA)-density tracks. The X and Y chromosomes are positioned at the end of the ideogram. Telomeric sequences were identified by searching the corresponding genome FASTA sequence file.
  </figcaption>
</figure>

<p><br></p>




<figure>
    <img src="Figure 5.jpg" style="width: 100%;" alt="Figure 2" />
  <figcaption aria-hidden="true">
    Figure 5: Ideogram of Triticum dicoccoides generated using the Genomic Ideogram plugin, with the genome sequence and GFF3 annotation file as inputs. Three genomic tracks are displayed: (1) (GA)₂₅₀ repeat bands along the chromosomes; (2) gene density; and (3) long non-coding RNA (lncRNA) density. U2 small nuclear RNA genes are additionally searched and displayed as feature labels along the chromosomes. Light-gray connector lines indicate genes located on the negative (−) strand, whereas dark-gray connector lines indicate genes located on the positive (+) strand.
  </figcaption>
</figure>

<p><br></p>




<figure>
    <img src="Figure 6.jpg" style="width: 100%;" alt="Figure 6" />
  <figcaption aria-hidden="true">
    Figure 6: Ideogram of Oryza sativa generated using the Genomic Ideogram plugin, with the genome sequence and GFF3 annotation file (v 1.0.63) as inputs. Three genomic tracks are displayed: (1) A centromeric repeat (AAACATGATTTTTGGACATATTGGAGTGTATTGGG; Max mismatch:2, Merge gap: 500, Min copies: 1) (A partial segment of AF058902, Dong et al., 1998, PNAS) bands along the chromosomes; (2) gene density; and (3) non-coding RNA (ncRNA) density. tRNA genes are additionally searched and displayed as feature labels along the chromosomes. Light-gray connector lines indicate genes located on the negative (−) strand, whereas dark-gray connector lines indicate genes located on the positive (+) strand.
  </figcaption>
</figure>

<p><br></p>



<figure>
    <img src="Figure 7.jpg" style="width: 100%;" alt="Figure 7" />
  <figcaption aria-hidden="true">
    Figure 7: Genomic distribution of candidate genes across  rice chromosomes, generated with the Genomic Ideogram plugin of IdeoKar2. Each chromosome is represented by three bars: Telomeric repeats, local gene density, and lncRNA density. Some genes are labeled with their gene symbol. Unlabeled symbols correspond to additional family members whose positions are shown but not individually named. Where multiple genes cluster within a short physical interval, their connector lines converge to a single locus on the chromosome to indicate tandem or closely linked arrangement.
  </figcaption>
</figure>

<p><br></p>

<figure>
    <img src="Figure 8.jpg" style="width: 100%;" alt="Figure 8" />
  <figcaption aria-hidden="true">
    Figure 7: Some other adjustments to the above case in figure 7.
  </figcaption>
</figure>

<p><br></p>


<figure>
    <img src="Figure 9.jpg" style="width: 100%;" alt="Figure 9" />
  <figcaption aria-hidden="true">
    Figure 9: The Ideogram panel showing circular genomic ideogram of  Plantago ovata generated using the Genomic Ideogram plugin, showing genomic features and intrachromosomal relationships generated by uploading MCScanX output. Some regions also highlighted by colored ribbons uploaded via 'Load Genomic ribbons CSV ...'. Gene density is shown as a blue-to-red track, together with an additional gene-density profile.
  </figcaption>
</figure>

<p><br></p>


<figure>
    <img src="Figure 10.jpg" style="width: 100%;" alt="Figure 10" />
  <figcaption aria-hidden="true">
    Figure 10: An example of the circular genomic ideogram for common wheat generated using the Genomic Ideogram plugin of IdeoKar2 showing chromosomal location of the wheat COL genes. Homoeologs are mapped to wheat chromosomes (composed of A, B, and D subgenomes) plus the unassembled (Un) part of the genome. Homoeologs were linked using curved lines (Ribbons). Chromosomes are banded by uploading cytoband svg file which shows banding according to pTa535-1 (red bands) and (GAA)10 (blue bands) FISH patterns. Chromosome number is indicated in the outside layer. Here, Bins per Mb was defined as 0.007 which divided each chromosome to 3 (1D) to 6 (3B) bins with different gene densities.
  </figcaption>
</figure>

<p><br></p>



#### Loading genomic data

**Load FASTA or ChrCoordinate** loads chromosome or scaffold sequences or a three column (chromosome, start, end) table of the chromosome length. If the genome FASTA sequence is loaded, it is also possible to search repeats or any other sequences and show them on chromosomes, **Load GFF3...** is optional but the features can be easily represented in separate track along the main chromosome.

The chromosome table contains Id (FASTA sequence identifier or chromosome name),
Genome (genome/sub-genome grouping label),
Display Name (chromosome label shown in the ideogram),
Length (bp) (sequence length), and 
Centromere (bp) (optional centromere position in the sequence, and Bands (number of repeat bands currently assigned to the chromosome).


#### Finding and adding repeat bands

The **Find a repeat and add it as a band** panel is activated if the genome FASTA sequence is loaded instead of the 3-column chromosome length table:
For repeat searching, choose **Selected chromosomes** in the **Search**
control to restrict **Find & Add Band** to the selected chromosome rows.
The same chromosome selection also controls **Generate Ideogram**: when
one or more chromosome rows are selected, **only those selected
chromosomes are drawn in the generated ideogram**. When the table
selection is cleared, the plugin returns to the default behavior of
drawing all loaded chromosomes.
This makes it possible, for example, to inspect or generate an ideogram
for a particular chromosome or subset of chromosomes without removing
the other chromosomes from the loaded dataset. Click **Generate Ideogram** to generate Ideogram.

## Citing IdeoKar2

A paper about IdeoKar2 has not been published yet. Meanwhile, if you use IdeoKar2 in a publication, please cite to the paper about the previous version:

Mirzaghaderi, G. & Marzangi, K. (2015). IdeoKar: an ideogram constructing and karyotype analyzing software. Caryologia, 68(1), 31-35. https://doi.org/10.1080/00087114.2014.998526


## Training video

https://www.youtube.com/watch?v=P-po20qPy2g


## Contact email

gh.mirzaghaderi@uok.ac.ir