![Version](https://img.shields.io/github/v/release/DCMLab/bach_en_fr_suites?display_name=tag)
[![DOI](https://zenodo.org/badge/388146263.svg)](https://doi.org/10.5281/zenodo.14996489)
![GitHub repo size](https://img.shields.io/github/repo-size/DCMLab/bach_en_fr_suites)
![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-9cf)


This is a README file for a data repository originating from the [DCML corpus initiative](https://github.com/DCMLab/dcml_corpora)
and serves as welcome page for both 

* the GitHub repo [https://github.com/DCMLab/bach_en_fr_suites](https://github.com/DCMLab/bach_en_fr_suites) and the corresponding
* documentation page [https://dcmlab.github.io/bach_en_fr_suites](https://dcmlab.github.io/bach_en_fr_suites)

For information on how to obtain and use the dataset, please refer to [this documentation page](https://dcmlab.github.io/bach_en_fr_suites/introduction).

When you use (parts of) this dataset in your work, please read and cite the accompanying data report:

_Hentschel, J., Rammos, Y., Neuwirth, M., & Rohrmeier, M. (2025). A corpus and a modular infrastructure for the 
empirical study of (an)notated music. Scientific Data, 12(1), 685. https://doi.org/10.1038/s41597-025-04976-z_

# J.S. Bach – English and French Suites (A corpus of annotated scores)

This corpus of annotated [MuseScore](https://musescore.org) files has been created within
the [DCML corpus initiative](https://github.com/DCMLab/dcml_corpora) and employs
the [DCML harmony annotation standard](https://github.com/DCMLab/standards).

Bach's English and French suites for keyboard likely date from some time around 
the same prolific Köthen period (1717-1723) as do the Sonatas and Partitas for solo violin and the Six Suites  
for solo cello, which are represented in [another DCML repository](https://github.com/DCMLab/bach_solo). All of these
works respond in some way to 
standard 18th-century courtly dance forms, though the music is, to varying degrees, inappropriate for dancing.  
Neither the titles "English" nor "French" convey any particular meaning, as all six suites evince varied influences  
and display similarly rich ornamentation. The English suites all include elaborate Preludes, a Bachian virtuosic  
specialty not necessarily characteristic of the Baroque as a whole, whereas the French suites consist instead in  
tauter, stricter interpretations of the dances. Our annotations reflect the precision-constructed harmonic framework  
from which Bach's virtuosic keyboard pyrotechnics are drawn and may be used fruitfully in examination of Bach's  
ornamentation practice.

## Getting the data

* download repository as a [ZIP file](https://github.com/DCMLab/bach_en_fr_suites/archive/main.zip)
* download a [Frictionless Datapackage](https://specs.frictionlessdata.io/data-package/) that includes concatenations
  of the TSV files in the four folders (`measures`, `notes`, `chords`, and `harmonies`) and a JSON descriptor:
  * [bach_en_fr_suites.zip](https://github.com/DCMLab/bach_en_fr_suites/releases/latest/download/bach_en_fr_suites.zip)
  * [bach_en_fr_suites.datapackage.json](https://github.com/DCMLab/bach_en_fr_suites/releases/latest/download/bach_en_fr_suites.datapackage.json)
* clone the repo: `git clone https://github.com/DCMLab/bach_en_fr_suites.git` 


## Data Formats

Each piece in this corpus is represented by five files with identical name prefixes, each in its own folder. 
For example, the *Prélude* of the first English Suite, BWV 806, has the following files:

* `MS3/BWV806_01_Prelude.mscx`: Uncompressed MuseScore 3.6.2 file including the music and annotation labels.
* `notes/BWV806_01_Prelude.notes.tsv`: A table of all note heads contained in the score and their relevant features (not each of them represents an onset, some are tied together)
* `measures/BWV806_01_Prelude.measures.tsv`: A table with relevant information about the measures in the score.
* `chords/BWV806_01_Prelude.chords.tsv`: A table containing layer-wise unique onset positions with the musical markup (such as dynamics, articulation, lyrics, figured bass, etc.).
* `harmonies/BWV806_01_Prelude.harmonies.tsv`: A table of the included harmony labels (including cadences and phrases) with their positions in the score.

Each TSV file comes with its own JSON descriptor that describes the meanings and datatypes of the columns ("fields") it contains,
follows the [Frictionless specification](https://specs.frictionlessdata.io/tabular-data-resource/),
and can be used to validate and correctly load the described file. 

### Opening Scores

After navigating to your local copy, you can open the scores in the folder `MS3` with the free and open source score
editor [MuseScore](https://musescore.org). Please note that the scores have been edited, annotated and tested with
[MuseScore 3.6.2](https://github.com/musescore/MuseScore/releases/tag/v3.6.2). 
MuseScore 4 has since been released which renders them correctly but cannot store them back in the same format.

### Opening TSV files in a spreadsheet

Tab-separated value (TSV) files are like Comma-separated value (CSV) files and can be opened with most modern text
editors. However, for correctly displaying the columns, you might want to use a spreadsheet or an addon for your
favourite text editor. When you use a spreadsheet such as Excel, it might annoy you by interpreting fractions as
dates. This can be circumvented by using `Data --> From Text/CSV` or the free alternative
[LibreOffice Calc](https://www.libreoffice.org/download/download/). Other than that, TSV data can be loaded with
every modern programming language.

### Loading TSV files in Python

Since the TSV files contain null values, lists, fractions, and numbers that are to be treated as strings, you may want
to use this code to load any TSV files related to this repository (provided you're doing it in Python). After a quick
`pip install -U ms3` (requires Python 3.10 or later) you'll be able to load any TSV like this:

```python
import ms3

labels = ms3.load_tsv("harmonies/BWV806_01_Prelude.harmonies.tsv")
notes = ms3.load_tsv("notes/BWV806_01_Prelude.notes.tsv")
```


## Version history

See the [GitHub releases](https://github.com/DCMLab/bach_en_fr_suites/releases).

## Questions, Suggestions, Corrections, Bug Reports

Please [create an issue](https://github.com/DCMLab/bach_en_fr_suites/issues) and/or feel free to fork and submit pull requests.

## Cite as

> Hentschel, J., Rammos, Y., Neuwirth, M., & Rohrmeier, M. (2025). A corpus and a modular infrastructure for the empirical study of (an)notated music. Scientific Data, 12(1), 685. https://doi.org/10.1038/s41597-025-04976-z

## License

Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License ([CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)).

![cc-by-nc-sa-image](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png)

## File naming convention

```regex
BWV(?<bwv>\d{3})_
(?<no>\d{2}a?)_
(?<movement>\S+)?
```

## Overview
|             file_name              |measures|labels|standard|                    annotators                     |   reviewers    |
|------------------------------------|-------:|-----:|--------|---------------------------------------------------|----------------|
|BWV806_01_Prelude                   |      37|   191|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |EMF, JH, DK     |
|BWV806_02_Allemande                 |      32|   145|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV806_03_Courante_I                |      20|    91|2.3.0   |Adrian Nagel (2.1.0), Ehsan Mohagheghi Fard (2.3.0)|EMF, DK         |
|BWV806_04_Courante_II               |      24|   104|2.3.0   |Davor Krkljus (2.3.0)                              |DK, EMF         |
|BWV806_05_Double_I                  |      24|   101|2.3.0   |Davor Krkljus (2.3.0)                              |DK              |
|BWV806_06_Double_II                 |      24|   100|2.3.0   |Davor Krkljus (2.3.0)                              |DK, EMF         |
|BWV806_07_Sarabande                 |      32|    72|2.3.0   |Davor Krkljus (2.3.0)                              |DK, EMF         |
|BWV806_08_Bouree_I                  |      48|   146|2.3.0   |Davor Krkljus (2.3.0)                              |DK, EMF         |
|BWV806_09_Bouree_II                 |      36|   126|2.3.0   |Davor Krkljus (2.3.0)                              |DK, EMF         |
|BWV806_10_Gigue                     |      40|   122|2.3.0   |Davor Krkljus (2.3.0)                              |DK, EMF         |
|BWV807_01_Prelude                   |     164|   564|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV807_02_Allemande                 |      24|   125|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV807_03_Courante                  |      24|   110|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV807_04_Sarabande                 |      28|    77|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus(2.3.0)         |DK, HB          |
|BWV807_04a_Agrements_de_la_Sarabande|      28|    79|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV807_05_Bourree_I                 |      56|   165|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV807_06_Bourree_II                |      24|    70|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, Hanné Becker|
|BWV807_07_Gigue                     |      74|   152|2.3.0   |Adrian Nagel (2.1.0), Hanné Becker (2.3.0)         |DK              |
|BWV808_01_Prelude                   |     213|   358|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV808_02_Allemande                 |      24|   121|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV808_03_Courante                  |      32|   153|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV808_04_Sarabande                 |      24|    44|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV808_04a_Agrements_de_la_Sarabande|      24|    51|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV808_05_Gavotte_I                 |      34|   108|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV808_06_Gavotte_II                |      16|    57|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV808_07_Gigue                     |      44|   208|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV809_01_Prelude                   |     108|   493|2.3.0   |Adrian Nagel (2.1.0), Hanné Becker (2.3.0)         |HB,  AN         |
|BWV809_02_Allemande                 |      24|    94|2.3.0   |Adrian Nagel (2.1.1), Hanné Becker (2.3.0)         |DK              |
|BWV809_03_Courante                  |      20|    67|2.3.0   |Adrian Nagel (2.1.1), Hanné Becker (2.3.0)         |DK              |
|BWV809_04_Sarabande                 |      24|    61|2.3.0   |Adrian Nagel (2.1.1), Hanné Becker (2.3.0)         |DK              |
|BWV809_05_Menuett_I                 |      32|    82|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV809_06_Menuett_II                |      32|    77|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV809_07_Gigue                     |      52|   195|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV810_01_Prelude                   |     156|   415|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV810_02_Allemande                 |      24|   130|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV810_03_Courante                  |      28|    84|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV810_04_Sarabande                 |      24|   101|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV810_05_Passepied_I               |      80|   218|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV810_06_Passepied_II              |      24|    65|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV810_07_Gigue                     |      96|   200|2.3.0   |Adrian Nagel (2.1.0), Hanné Becker (2.3.0)         |DK              |
|BWV811_01_Prelude                   |     195|   610|2.3.0   |Adrian Nagel (2.1.0), Hanné Becker (2.3.0)         |DK              |
|BWV811_02_Allemande                 |      24|   111|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, Hanné Becker|
|BWV811_03_Courante                  |      32|   132|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, Hanné Becker|
|BWV811_04_Sarabande                 |      24|    60|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, Hanné Becker|
|BWV811_05_Double                    |      24|    64|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV811_06_Gavotte_I                 |      32|   102|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV811_07_Gavotte_II                |      24|    77|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV811_08_Gigue                     |      56|   241|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV812_01_Allemande                 |      24|   133|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV812_02_Courante                  |      24|   101|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV812_03_Sarabande                 |      24|    79|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV812_04_Menuett_I                 |      24|    57|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV812_05_Menuett_II                |      40|    66|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV812_06_Gigue                     |      28|   125|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, HB          |
|BWV813_01_Allemande                 |      18|   123|2.3.0   |Arne Lüthke (2.1.0), Amelia Brey (2.3.0)           |AB, ST          |
|BWV813_02_Courante                  |      57|   168|2.3.0   |Arne Lüthke (2.1.0), Amelia Brey (2.3.0)           |AB, ST          |
|BWV813_03_Sarabande                 |      24|   102|2.3.0   |Arne Lüthke (2.1.0), Amelia Brey (2.3.0)           |AB, ST          |
|BWV813_04_Air                       |      16|   105|2.3.0   |Arne Lüthke (2.1.0), Amelia Brey (2.3.0)           |AB, ST          |
|BWV813_05_Menuett                   |      32|    74|2.3.0   |Arne Lüthke (2.1.0), Amelia Brey (2.3.0)           |AB, ST          |
|BWV813_06_Gigue                     |      84|   141|2.3.0   |Arne Lüthke (2.1.0), Amelia Brey (2.3.0)           |AB, ST          |
|BWV814_01_Allemande                 |      24|   163|2.3.0   |Adrian Nagel (2.1.0), Sylvie Tran (2.3.0)          |ST, AB          |
|BWV814_02_Courante                  |      28|   109|2.3.0   |Adrian Nagel (2.1.0), Sylvie Tran (2.3.0)          |ST, AB          |
|BWV814_03_Sarabande                 |      24|    85|2.3.0   |Adrian Nagel (2.1.0), Sylvie Tran (2.3.0)          |ST, AB          |
|BWV814_04_Gavotte                   |      32|   100|2.3.0   |Adrian Nagel (2.1.0), Sylvie Tran (2.3.0)          |ST, AB          |
|BWV814_05_Menuett                   |      36|    94|2.3.0   |Adrian Nagel (2.1.0), Sylvie Tran (2.3.0)          |ST, AB          |
|BWV814_06_Trio                      |      24|    63|2.3.0   |Adrian Nagel (2.1.0), Sylvie Tran (2.3.0)          |ST, AB          |
|BWV814_07_Gigue                     |      68|   155|2.3.0   |Adrian Nagel (2.1.0), Sylvie Tran (2.3.0)          |ST, AB          |
|BWV815_01_Allemande                 |      20|   104|2.3.0   |Ehsan Mohagheghi Frad (2.3.0)                      |EMF, DK         |
|BWV815_02_Courante                  |      36|    89|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV815_03_Sarabande                 |      24|    63|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV815_04_Gavotte                   |      22|    85|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV815_05_Air                       |      22|    80|2.3.0   |Ehsan Mohagheghi Fard 82.3.0)                      |EMF, DK         |
|BWV815_06_Menuett                   |      16|    45|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV815_07_Gigue                     |      60|   106|2.3.0   |Ehsan Mohagheghi Fard (2.3.0)                      |EMF, DK         |
|BWV816_01_Allemande                 |      24|   142|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV816_02_Courante                  |      32|    83|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV816_03_Sarabande                 |      40|   106|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV816_04_Gavotte                   |      24|    68|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV816_05_Bourree                   |      30|    77|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV816_06_Loure                     |      16|    66|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV816_07_Gigue                     |      56|   162|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV817_01_Allemande                 |      28|   103|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV817_02_Courante                  |      32|    94|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV817_03_Sarabande                 |      24|    65|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV817_04_Gavotte                   |      20|    58|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV817_05_Polonaise                 |      24|    67|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV817_06_Bourree                   |      42|   122|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV817_07_Gigue                     |      48|   116|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |
|BWV817_08_Menuett                   |      24|    49|2.3.0   |Adrian Nagel (2.1.0), Davor Krkljus (2.3.0)        |DK, ST          |


*Overview table automatically updated using [ms3](https://ms3.readthedocs.io/).*
