# KGLW Bingo Generator

[King Gizzard and Lizard Wizard](https://kinggizzardandthelizardwizard.com/) is known for having a large catalog of songs and for changing up the setlists of their live shows constantly. Try playing BINGO/GIZZO at one of their shows!

A hundred pre-made bingo cards are available as PDFs in the folder `output/`. 
* `popularity` cards choose songs based on popularity.
* `year` cards choose songs based on year of release, with more recent songs favored.
* `hybrid` cards choose songs based on a mix of popularity and release year.
* `none` cards choose songs purely at random.

The extended mixes on *The Silver Cord* were considered duplicate songs and not included.

Last updated: August 12, 2024

Last album included: *Flight b741*

## Example:

![](output/sample.png?raw=true)

## How to generate your own Bingo cards

Create a python environment that has `numpy`, `pandas`, `shutil`, `re`, `BeautifulSoup`, `argparse`, `matplotlib` and `textwrap`. Most of these packages should come in standard python distributions.

Run `src/generate_bingo.py` with the following arguments:

```
    -f, --filename: str. Prefix for output filename. Writes to output/.
        Default: "output".
    -t, --top_word: str. Word at the top of card. E.g. GIZZO, BINGO, etc.
        Default: "GIZZO"
    -w, --weight: str. What type of weighting to use for random selection of songs.
        'popularity': Weight songs by number of plays on YouTube Music.
        'year': Weight songs by how recently they were released (more recent songs = more likely to show up on card).
        'hybrid': Weight songs by average of popularity weight and year weight.
        'none': Each song is equally likely to appear.
    -s, --seed: int. Seed for numpy.random.
    --no_album_covers: Add this flag to not include album covers in bingo card.
```

## Examples:

### Card with weighting by year, album covers included, 'BINGO' at top of card and file prefix 'nonagon'

`python generate_bingo.py -f nonagon -t BINGO -w year`

### Card with hybrid weighting, album covers included, 'GIZZO' at top of card and file prefix 'gizzo'

`python generate_bingo.py -f gizzo -t GIZZO -w hybrid`

### Card with weighting by popularity, album covers not included, 'GIZZO' at top of card and file prefix 'gizzo'

`python generate_bingo.py -f gizzo -t GIZZO -w popularity --no_album_covers`

### Card with no weighting, album covers included, 'GIZZO' at top of card and file prefix 'gizzo', generated with seed=741

`python generate_bingo.py -f gizzo -t GIZZO -w none -s 741`


