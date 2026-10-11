# Appliance Energy Consumption Website: Televisions

COS30045 Data Visualisation, Exercise 3 (Communicating data insights)
Author: Pham Anh (105977992), Swinburne Vietnam

**Question:** Does the screen technology of a television (LCD, LCD (LED) or OLED) change how much electricity it uses?

## Pages

| Page | Purpose |
| --- | --- |
| `index.html` | Hook, key numbers and FAQ for general readers |
| `televisions.html` | Data cleaning (KNIME) and the six-step analysis |
| `storyboard.html` | Audience, design guidelines and storyboard of the user experience |
| `about.html` | Author, data, limitations, AI use |

## Data Story

### Audience
**Primary audience:** Australian households who are about to buy a TV and want to keep running costs down. They are not data specialists. They know the energy label (stars and kWh per year) but not how screen technology relates to it. They decide quickly, often on a phone or laptop in a shop or at home.

**Secondary audience:** a tutor or marker who wants to see clear design decisions, not technical detail.

### What they want to know
1. Will an OLED (or LED LCD) TV cost me more to run than an LCD?
2. Is the difference caused by the technology, or by something else?
3. What should I compare when I choose a TV?

### The story (arc)
| Step | Message | Chart |
| --- | --- | --- |
| Setup | Three screen technologies are on sale; LCD (LED) dominates (81%). | Fig 2, bar chart |
| Conflict | LCD looks cheapest to run (median 296 kWh/year vs 408 and 422). | Fig 3, box plot + table |
| Twist | LCD TVs are smaller (51 vs 65 inches on average), so the comparison is unfair. | Table |
| Resolution | Per 100 cm² of screen the three are almost equal (4.11, 4.16, 4.00 kWh/year). At the same size they are close too. | Fig 4 and Fig 5 |
| Check | In-use power and star ratings tell the same story. | Fig 6 and Fig 7 |
| Call to action | Choose the size you need, then compare kWh per year of models at that size. | Conclusion |

### Design guidelines
- One message per chart, with a plain-English insight sentence under each figure.
- Same colour for the same technology on every chart.
- Show the unfair raw comparison first, then correct it, so readers see why size matters.
- Flag small groups (for example the over 100 inch band has only 30 models) instead of hiding them.
- Alt text on every chart; headings in order; sufficient colour contrast.

## About the data

### Data source
Energy rating data for labelled televisions from the Australian Government GEMS product registration database, published on data.gov.au: https://data.gov.au/data/dataset/energy-rating-for-household-appliances. File used: `tv_2026_10_02.csv` (5,030 models, 32 columns). The column meanings come from the data dictionary `televisionsmay2015.docx`.

### Data processing
Done in KNIME (see Figure 1 on the Televisions page):
1. Kept `Availability Status = Available` (removed 11 models).
2. Kept models where `SoldIn` contains "Australia" (removed 180 models sold only in New Zealand, or Fiji and New Zealand).
3. Kept only the columns needed: brand, model, screen size, screen area, screen technology, in-use power, Star2 and labelled energy consumption.
4. Checked quality: three consistent `Screen_Tech` values, no missing energy values, `SubmitStatus` is "Approved" for every row.
5. Created `kwh_per_100cm2` (kWh/year divided by screen area, times 100), `size_inch` (cm divided by 2.54), `size_band` and `stars_5plus` (Star2 of 5 or more).

Result: 4,839 models (3,940 LCD (LED), 607 LCD, 292 OLED).

### Privacy
The dataset describes products (brands, models, energy figures), not people. It contains no personal data. Product and brand website URLs are public company addresses and were dropped from the analysis.

### Accuracy and limitations
- Energy use is the **labelled** kWh per year from a standard test, not measured use in a real home. Real use depends on viewing hours, brightness settings and content.
- Figures are reported by manufacturers or registrants when they register a model. Availability is self-reported.
- 228 rows share a brand and model number with another row. They are kept as separate registrations.
- Some groups are small: OLED has no models up to 32 inches or at 66 to 75 inches, there are few LCD models at very large sizes, and the over 100 inch band has only 30 models. Comparisons there are less reliable.
- The data dictionary is dated May 2015 and the file is from 2026, so some columns differ (for example the labelled energy column replaces CEC, and two standby descriptions in the dictionary look swapped). Only columns whose meaning is clear were used.
- The analysis shows association at the same size, not proof that technology has no effect.

### Ethics
- Brands are not ranked or praised, to avoid implying endorsement.
- Charts use honest axes (bars start at zero) and show the unfair raw comparison alongside the corrected one.
- Uncertainty and small samples are stated in the text.
- The data is open government data, cited with its source.

## AI Declaration
Generative AI was used to help draft the website structure, CSS, JavaScript. I reviewed and edited the output, checked figures against the KNIME results and take responsibility for the final content.
