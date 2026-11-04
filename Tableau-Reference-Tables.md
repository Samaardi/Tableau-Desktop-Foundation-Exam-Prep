# Tableau Reference Tables

The key comparison tables for the **Salesforce Certified Tableau Desktop Foundations** exam, in the same order as the decks on the [flashcard site](https://samaardi.github.io/Tableau-Desktop-Foundation-Exam-Prep/). The exam is closed-book and based on **Tableau 2022.3**, so these are worth knowing by heart. Every entry was checked against the Salesforce exam guide and Tableau Desktop help.

## Contents

| Group | Sections |
| --- | --- |
| Getting started | [Exam format](#exam-format-and-strategy) · [Workspace](#workspace-and-interface) |
| 1 · Connecting to and preparing data (23%) | [Connections and extracts](#live-connections-and-extracts) · [Cleaning](#cleaning-and-shaping-data) · [Data model](#relationships-joins-and-unions) · [Field properties](#field-properties) |
| 2 · Exploring and analyzing data (37%) | [Charts](#basic-charts) · [Maps](#maps) · [Axes](#combined-and-dual-axis) · [Groups, sets, hierarchies](#groups-sets-and-hierarchies) · [Filters](#filters-and-order-of-operations) · [Dates](#dates-and-date-filters) · [Sorting and totals](#sorting-and-totals) · [Analytics](#reference-lines-and-analytics) · [Table calcs](#quick-table-calculations) · [Bins](#bins-and-histograms) · [Calculated fields](#calculated-fields) · [Parameters](#parameters) |
| 3 · Sharing insights (25%) | [Formatting](#formatting) · [Dashboards](#dashboards-and-layout) · [Actions](#actions-and-interactivity) · [Stories](#stories) · [Sharing](#sharing-and-exporting) |
| 4 · Understanding Tableau concepts (15%) | [Dimensions and measures](#dimensions-and-measures) · [Discrete and continuous](#discrete-and-continuous) · [Aggregation](#aggregation-and-level-of-detail) |
| Practice | [Common exam scenarios](#common-exam-scenarios) |

---

# Getting started

## Exam format and strategy

| | |
| --- | --- |
| Exam | Salesforce Certified Tableau Desktop Foundations (Analytics-101), formerly Tableau Desktop Specialist |
| Questions | 40 scored, plus up to 5 unscored (not marked) |
| Question types | Multiple choice and multiple select |
| Time | 70 minutes, about 90 seconds per question |
| Passing score | 48% (about 20 of 40) |
| Fee | 75 USD plus tax; retakes free |
| Delivery | Proctored online or at a test centre |
| Materials allowed | None; Tableau is not available |
| Tableau version | 2022.3 |
| Recommended experience | At least 3 months of hands-on Tableau Desktop |

| Domain | Weight | About |
| --- | --- | --- |
| 1. Connecting to and preparing data | 23% | 9 questions |
| 2. Exploring and analyzing data | 37% | 15 questions |
| 3. Sharing insights | 25% | 10 questions |
| 4. Understanding Tableau concepts | 15% | 6 questions |

Strategy: answer the easy questions first and flag the rest. In multiple-select questions, choose exactly the number asked, and watch for **NOT**, **CANNOT** and **EXCEPT**. Never leave a question blank.

## Workspace and interface

| Part | What it is |
| --- | --- |
| Start page | Connect, Open and Discover panes; the Tableau icon on the toolbar returns to it |
| Data pane | Fields grouped by table; dimensions above the line, measures below; parameters at the bottom |
| Analytics pane | Drag-in reference lines, trend lines, forecasts, totals, clusters |
| Shelves | Columns, Rows, Filters, Pages |
| Pages shelf | One page per value, with a player to step through them |
| Marks card | Mark type plus Color, Size, Label, Detail, Tooltip (and Shape, Path, Angle) |
| Show Me | Chart picker; the recommended chart has an orange outline |
| Status bar | Number of marks, rows and columns, and the SUM of the measure |
| Special values indicator | “12 nulls” or “5 unknown”: filter, show at default position, or edit locations |

| Toolbar button | Does |
| --- | --- |
| Pause Auto Updates / Run Update | Stop querying after every change / run the query once |
| New Worksheet (drop-down) | New worksheet, dashboard or story |
| Duplicate | Copy the current sheet |
| Clear (drop-down) | Clear the sheet, or only filters, formatting, sizing or axis ranges |
| Swap | Swap Rows and Columns |
| Sort Ascending / Descending | Sort by the measure in the view |
| Group Members | Group the selected values |
| Show Mark Labels | Turn labels on or off |
| Fix Axes | Lock or unlock the axis range |
| Fit | Standard, Fit Width, Fit Height, Entire View |
| Presentation Mode | Show only the view |

| Shortcut (Windows) | Action |
| --- | --- |
| Ctrl+D | Connect to data |
| Ctrl+M | New worksheet |
| Ctrl+W | Swap rows and columns |
| Ctrl+1 | Show Me |
| Ctrl+E | Describe sheet |
| F5 | Refresh data source |
| F7 or Ctrl+H | Presentation mode |
| F9 / F10 | Run update / pause auto updates |
| Ctrl+Z / Ctrl+Y | Undo / redo (back to when the workbook was opened) |
| Ctrl+drag | Copy a pill |
| Right-drag (Option-drag on Mac) | Drop Field menu: choose aggregation or date level |

---

# 1 · Connecting to and preparing data (23%)

## Live connections and extracts

| | Live connection | Extract |
| --- | --- | --- |
| Where the data is | Stays in the source; Tableau queries it every time the view changes | A compressed snapshot saved in a `.hyper` file |
| How current | Always up to date | Only as current as the last refresh |
| Speed | Depends on the database | Usually fast |
| Works offline | No | Yes |
| Best when | You need real-time data, the database is fast, or data can't be copied out | The source is slow, you work offline, you need a subset, or you publish to Tableau Public |
| How to set it | Data Source page > **Live** (the default) | Data Source page > **Extract**, or Data > *source* > **Extract Data…** |

| Extract option | Does |
| --- | --- |
| Filters | Keep only some rows (extract filter) |
| Aggregate data for visible dimensions | Roll rows up, optionally to a date level |
| Number of rows | All rows (with optional incremental refresh), Top N, or Sample |
| Hide All Unused Fields | Leave out fields not used in the workbook |
| Data storage | Single table or multiple tables |

| Refresh | What it does |
| --- | --- |
| Full | Replaces all data in the extract |
| Incremental | Adds only new rows, based on a column that increases (date or ID); doesn't update changed or deleted rows |

| Task | Menu path |
| --- | --- |
| Refresh an extract | Data > *source* > Extract > **Refresh** |
| Back to live | Right-click the source > Extract > **Remove**, or untick **Use Extract** |
| Save metadata as `.tds` | Right-click the source > **Add to Saved Data Sources…** |
| Add a second connection | Data Source page > **Add** next to Connections |

| Extension | Name | Contains data? | Use it to |
| --- | --- | --- | --- |
| `.twb` | Workbook | No, only a link to the source | Share with people who can reach the same data |
| `.twbx` | Packaged workbook | Yes: extracts, local files, images | Share with anyone, open in Tableau Reader |
| `.tds` | Data source | No, connection info and metadata | Reuse calculated fields, aliases, groups and default properties |
| `.tdsx` | Packaged data source | Yes | Reuse a data source with its local data |
| `.hyper` | Extract | Yes | Store extract data (older versions used `.tde`) |
| `.tbm` | Bookmark | Depends | Copy one worksheet into another workbook |

## Cleaning and shaping data

| Tool | Where | Use it when |
| --- | --- | --- |
| Data Interpreter | Data Source page > **Use Data Interpreter** | Excel, CSV, PDF or Google Sheets files have titles, notes or blank rows |
| Pivot | Select columns > right-click > **Pivot** | The same measure is spread across columns (one per month or year); creates Pivot Field Names and Pivot Field Values |
| Split / Custom Split | Right-click a field > **Transform** | One column holds two values, e.g. “Smith, Anna” |
| Data source filter | Data Source page > **Filters > Add** | Every sheet should see only some rows |
| Replace Data Source | Data > **Replace Data Source…** | Point the workbook at another source with the same fields |
| Edit Connection | Data Source page > Edit Connection | Point at a new copy of the same file |

| | Extract filter | Data source filter |
| --- | --- | --- |
| Limits | Rows that go into the extract | Rows for all sheets using the data source |
| Works with | Extracts only | Live connections and extracts |
| Runs | First | Second, before any worksheet filter |

## Relationships, joins and unions

| Method | Layer | Result | Choose it when |
| --- | --- | --- | --- |
| Relationship | Logical | Tables stay separate; Tableau picks the join at query time | Default choice; tables at different levels of detail |
| Join | Physical | Columns added side by side on a key | You need control of the join type, or one flat table |
| Union | Physical | Rows stacked on top of each other | Tables have the same columns (e.g. one sheet per year) |
| Blend | Worksheet | Secondary source aggregated, then combined like a left join | Two separate data sources, set up per sheet |

| Join | Keeps |
| --- | --- |
| Inner | Only rows that match in both tables |
| Left | All rows from the left table, plus matches from the right (no match = null) |
| Right | All rows from the right table, plus matches from the left |
| Full outer | All rows from both tables |

| Detail | Value |
| --- | --- |
| Open the physical layer | Double-click a logical table |
| Join clause operators | `=`, `<>`, `<`, `<=`, `>`, `>=`, or a join calculation |
| Relationship defaults (Performance Options) | Cardinality Many to Many; referential integrity Some records match |
| Union source fields | Sheet and Table Name (Excel), Path and Table Name (files) |
| Columns named differently in a union | Select them > **Merge Mismatched Fields** |
| Wildcard union | Picks files or sheets by name pattern, e.g. `Orders*` |
| Blend icons | Primary source: blue check; secondary: orange check; linking field: orange chain |

## Field properties

| Data type | Icon |
| --- | --- |
| String | Abc |
| Number (decimal / whole) | # |
| Date | Calendar |
| Date & Time | Calendar with clock |
| Boolean | T\|F |
| Geographic | Globe |

| Field type | Default properties you can set |
| --- | --- |
| Dimension | Comment, Color, Shape, Sort, Aliases |
| Measure | Comment, Color, Number Format, Aggregation, Total Using |
| Date | Date Format, Fiscal Year Start (plus the dimension properties) |

| Task | How | Note |
| --- | --- | --- |
| Rename a field | Right-click > Rename | Source data is unchanged |
| Alias a value | Right-click > Aliases… | Not for measures, continuous fields or dates |
| Geographic role | Right-click > Geographic Role | Creates Latitude and Longitude (generated) |
| Change data type | Click the type icon, or right-click > Change Data Type | |
| Number to dimension | Right-click > Convert to Dimension | For IDs and postal codes |
| Hide a field | Right-click > Hide | Hidden fields are left out of extracts |
| Folders | Data pane menu > Group by Folder | |

Geographic roles: Airport, Area Code (U.S.), CBSA/MSA (U.S.), City, Congressional District (U.S.), Country/Region, County, NUTS Europe, State/Province, ZIP Code/Postcode, plus Latitude and Longitude.

---

# 2 · Exploring and analyzing data (37%)

## Basic charts

| Chart | How to build it | Show Me needs |
| --- | --- | --- |
| Bar | Dimension on Rows, measure on Columns | 0+ dimensions, 1+ measures |
| Stacked bar | Bar chart + a dimension on Color | 1+ dimensions, 1+ measures |
| Side-by-side bar | Two dimensions on the same shelf, measure on the other | 1+ dimensions, 1+ measures |
| Line | Date on Columns, measure on Rows | 1 date, 0+ dimensions, 1+ measures |
| Scatter plot | Measure on Rows and measure on Columns; dimension on Detail | 0+ dimensions, 2–4 measures |
| Text table | Dimensions on Rows and Columns, measure on Text | 1+ dimensions, 1+ measures |
| Highlight table | Text table + measure on Color, mark type Square | 1+ dimensions, 1 measure |
| Heat map | Squares sized and coloured by measures | 1+ dimensions, 1–2 measures |
| Treemap | Dimension on Detail/Label, measure on Size and Color | 1+ dimensions, 1–2 measures |
| Pie | Mark type Pie; dimension on Color, measure on Angle | 1+ dimensions, 1–2 measures |
| Box plot | Median, quartiles, whiskers to 1.5 × IQR | 1+ measures |
| Bullet graph | Actual as bar, target as reference line, distribution bands | 0+ dimensions, 2 measures |
| Gantt | Mark type Gantt Bar; date on Columns, duration on Size | 1 date, 1+ dimensions |

| Fields on Rows and Columns | Automatic mark type |
| --- | --- |
| Dimension + measure | Bar |
| Date + measure | Line |
| Measure + measure | Shape (scatter plot) |
| Dimensions only | Text |

Mark types: Automatic, Bar, Line, Area, Square, Circle, Shape, Text, Map, Pie, Gantt Bar, Polygon, Density.

| Marks card button | Does |
| --- | --- |
| Color | Colour by a field |
| Size | Size by a field, or a slider |
| Label | Show values on marks |
| Detail | More marks without colour or headers (changes level of detail) |
| Tooltip | Text shown on hover |
| Shape / Path / Angle | Only for Shape, Line/Polygon and Pie marks |

## Maps

| Map | How | Use it for |
| --- | --- | --- |
| Point (symbol) map | Double-click a geographic field; measure on Size | Amounts at points; the usual default |
| Filled map | Mark type **Map**; measure on Color | A value or rate per area; not for City or Airport |
| Density map | Mark type **Density**; adjust Color > Intensity | Many overlapping points |
| Your own coordinates | Fields with Latitude and Longitude roles as dimensions, or an ID on Detail | Exact locations |

| Double-clicking a geographic field puts | |
| --- | --- |
| Longitude (generated) | Columns |
| Latitude (generated) | Rows |
| The geographic field | Detail |

| Map menu | Does |
| --- | --- |
| Edit Locations… | Match names Tableau didn't recognise (also via “N unknown”) |
| Background Maps | Light, Dark, Streets, Satellite and others |
| Map Layers… | Borders, labels, coastlines, data layers |
| Map Options… | Allow pan and zoom, show map search, show toolbar |

## Combined and dual axis

| | Dual axis | Combined (shared) axis |
| --- | --- | --- |
| Axes | Two: left and right | One |
| Marks cards | One per measure (plus All) | One |
| Mark types | Can differ (bar + line) | Same for all |
| Number of measures | Two | Many |
| How | Right-click the second pill > **Dual Axis** | Drag the second measure onto the existing axis |
| Fields used | The two measures | Measure Names + Measure Values |
| Best when | Measures have different units | Measures have the same units |

Same scale on both axes: right-click the secondary axis > **Synchronize Axis**. Hide it: right-click > untick **Show Header**.

## Groups, sets and hierarchies

| | Group | Set |
| --- | --- | --- |
| What it does | Combines values into new categories | Splits values into In and Out |
| Values | As many as you make (+ optional "Other") | Two: In / Out |
| Dynamic? | No | Yes, if computed by condition or Top N |
| Icon | Paperclip | Venn diagram |
| Create from | Data pane, headers, or marks | Data pane, or selected marks |
| In calculations | Like any dimension | TRUE for members |

| Set dialog tab | Defines members by |
| --- | --- |
| General | Ticking values (fixed set) |
| Condition | A rule, e.g. SUM(Profit) > 0 |
| Top | Top or bottom N by a field |

| Combined set option | Keeps |
| --- | --- |
| All members in both sets | Union of the two sets |
| Shared members in both sets | Only members in both |
| Left set except shared members | Left set minus the right |
| Right set except shared members | Right set minus the left |

Hierarchy: drag one dimension onto another (or right-click > Hierarchy > Create Hierarchy). Drill with **+** and **−**. Dates get a hierarchy automatically: Year > Quarter > Month > Day.

## Filters and order of operations

| Filter | Where you create it | Notes |
| --- | --- | --- |
| Extract | Extract dialog | Limits rows in the extract |
| Data source | Data Source page > Filters | Applies to all sheets using the source |
| Context | Right-click a filter > **Add to Context** | Grey pill; runs before Top N, sets, conditional filters and FIXED |
| Dimension | Filters shelf | Tabs: General, Wildcard, Condition, Top |
| Measure | Filters shelf | Range, At least, At most, Special |
| Date | Filters shelf | Relative date, Range of dates, date parts, Individual dates |
| Table calculation | Filters shelf with a table calc | Acts last; only hides marks |

| Dimension filter tab | Example |
| --- | --- |
| General | Tick Furniture and Technology |
| Wildcard | Product Name contains “Chair” |
| Condition | SUM(Sales) > 10,000 |
| Top | Top 10 by SUM(Profit) |

| Filter card option | Does |
| --- | --- |
| All values in database | Always lists every value |
| Only relevant values | Lists only values possible after other filters |
| Show (All) value, search, Apply button | Customise the card |
| Include / Exclude values | Turn the selection into an exclusion |

| Apply to Worksheets | Filter affects |
| --- | --- |
| Only This Worksheet | The current sheet (default) |
| Selected Worksheets… | Sheets you choose |
| All Using This Data Source | Every sheet on this source |
| All Using Related Data Sources | Every sheet on related sources |

| Step | Order of operations |
| --- | --- |
| 1 | Extract filters |
| 2 | Data source filters |
| 3 | Context filters |
| 4 | Sets, conditional and Top N filters, FIXED LOD expressions |
| 5 | Dimension filters |
| 6 | Data blending |
| 7 | INCLUDE and EXCLUDE LOD expressions |
| 8 | Measure filters |
| 9 | Forecasts, table calculations, clusters, totals |
| 10 | Trend lines and reference lines |

Filters on table calculations only hide marks after the calculation is done, so they act last. Top N filters don't see ordinary dimension filters; add the dimension filter to context to make Top N respect it.

## Dates and date filters

| | Date part (discrete) | Date value (continuous) |
| --- | --- | --- |
| Pill | Blue | Green |
| In the date menu | Upper group: Year, Quarter, Month, Day | Lower group: e.g. Month May 2015 |
| Shows | Headers; all Januaries combined | An axis; each month of each year separate |
| Use it for | Seasonality, comparing years | Trends over the whole period |
| Default when you drag a date | YEAR(Order Date) | |

| Date filter option | Example |
| --- | --- |
| Relative dates | Last 3 months, this year, year to date (moves with today) |
| Range of dates | 1 Jan 2025 – 30 Jun 2025 |
| Starting date / Ending date | From 1 Jan 2025 on |
| Date part | Years, Quarters, Months, Days… |
| Individual dates | Tick exact dates |

| Function | Returns | Example result |
| --- | --- | --- |
| `DATEPART('month', [Order Date])` | Integer | 3 |
| `DATENAME('month', [Order Date])` | String | March |
| `DATETRUNC('month', [Order Date])` | Date | 1 March 2025 |
| `DATEDIFF('day', [Order Date], [Ship Date])` | Integer | 4 |
| `DATEADD('month', 3, [Order Date])` | Date | 3 months later |
| `YEAR()`, `MONTH()`, `DAY()` | Integer | 2025 |
| `TODAY()` / `NOW()` | Date / Date & Time | Current date / date and time |
| `DATEPARSE("MMM yyyy", [Month])` | Date | Turns the text “Jan 2025” into a date |

| Task | How |
| --- | --- |
| A field at one fixed date level | Right-click the date > Create > **Custom Date…** |
| Show months with no data | Right-click the date header > **Show Missing Values** |
| Fiscal year | Default Properties > **Fiscal Year Start** |

## Sorting and totals

| Sort method | How | Updates with data? |
| --- | --- | --- |
| Toolbar sort | Sort Ascending / Descending buttons | Yes (by the measure) |
| Axis or header sort icon | Click the icon | Yes |
| Drag headers | Drag to a new position | No (manual) |
| Sort dialog | Right-click the dimension > Sort… | Depends on the option |

| Sort dialog option | Sorts by |
| --- | --- |
| Data source order | Order in the source |
| Alphabetic | A–Z or Z–A |
| Field | Any measure and aggregation, even one not in the view |
| Manual | An order you set |
| Nested | The inner dimension within each value of the outer one |

| Totals task | Menu path |
| --- | --- |
| Grand totals | Analysis > Totals > Show Column / Row Grand Totals |
| Subtotals | Analysis > Totals > Add All Subtotals |
| Move totals | Analysis > Totals > Column Totals to Top / Row Totals to Left |
| Change how a total is calculated | Right-click the pill > Total Using (default Automatic) |

## Reference lines and analytics

| Analytics pane section | Items |
| --- | --- |
| Summarize | Constant Line, Average Line, Median with Quartiles, Box Plot, Totals |
| Model | Average with 95% CI, Median with 95% CI, Trend Line, Forecast, Cluster |
| Custom | Reference Line, Reference Band, Distribution Band, Box Plot |

| Item | Shows | Example |
| --- | --- | --- |
| Reference line | One value | Average sales |
| Reference band | Shaded area between two values | Between min and max |
| Distribution band | Shaded ranges from a distribution | 60% and 80% of average, percentiles, standard deviations |

| Reference line setting | Options |
| --- | --- |
| Scope | Entire Table, Per Pane, Per Cell |
| Value | Constant, aggregation (Total, Sum, Minimum, Maximum, Average, Median), or a parameter |
| Needs | A continuous axis |

| Model | Needs | Notes |
| --- | --- | --- |
| Trend line | Numeric fields on both axes (two measures, or a continuous date and a measure) | Linear, Logarithmic, Exponential, Power, Polynomial; Describe Trend Line shows R-squared and p-value |
| Forecast | A date and a measure | Exponential smoothing; Analysis > Forecast > Forecast Options |
| Cluster | Measures in the view | k-means; drag the result to the Data pane to save it as a group |

## Quick table calculations

| Calculation | Answers |
| --- | --- |
| Running Total | What is the cumulative total so far? |
| Difference | How much did it change from the previous value? |
| Percent Difference | By what % did it change from the previous value? |
| Percent of Total | What share of the total is this mark? |
| Rank | Where does this mark rank? |
| Percentile | What percentile is this mark in? |
| Moving Average | What is the average of the last few values? (default: previous 2 and current) |
| YTD Total | What is the total so far this year? |
| Compound Growth Rate | What is the average growth rate per period? |
| Year over Year Growth | How much did it grow compared with the same period last year? |
| YTD Growth | How does year-to-date compare with last year's year-to-date? |

| Compute Using | Direction |
| --- | --- |
| Table (across) | Left to right across the whole table |
| Table (down) | Top to bottom across the whole table |
| Table (across then down) | Across, then down to the next row |
| Pane (across / down) | Within each pane only |
| Cell | Each cell on its own |
| Specific Dimensions | The dimensions you tick |

| Task | How |
| --- | --- |
| Add | Right-click a measure pill > Quick Table Calculation |
| Edit | Right-click the Δ pill > Edit Table Calculation… |
| Remove | Right-click > Clear Table Calculation |
| Save as a calculated field | Drag the Δ pill into the Data pane |

## Bins and histograms

| | Bar chart | Histogram |
| --- | --- | --- |
| X axis | Categories (a dimension) | Numeric ranges (bins) of one measure |
| Y axis | A measure | Count of values in each bin |
| Answers | How do categories compare? | How are values distributed? |

| Task | How |
| --- | --- |
| Create bins | Right-click a numeric field > Create > Bins… (or Suggest Bin Size) |
| Result | A discrete dimension, e.g. Sales (bin) |
| Change size | Right-click the bin > Edit…; the size can be a parameter |
| Histogram from Show Me | Select one measure > Histogram: bin on Columns, CNT on Rows |
| Bin label | The lower edge: “100” means 100 up to 200 |

## Calculated fields

| Function | Use |
| --- | --- |
| `IF … THEN … ELSEIF … ELSE … END` | Several conditions |
| `IIF(test, then, else)` | Short IF |
| `CASE [field] WHEN … THEN … END` | Compare one field to values |
| `IFNULL([x], 0)` | Replace null with a value |
| `ZN([x])` | Replace null with zero |
| `ISNULL([x])` | TRUE if null |
| `AND`, `OR`, `NOT` | Combine conditions |

| Kind | Functions |
| --- | --- |
| String | `LEFT`, `RIGHT`, `MID`, `LEN`, `UPPER`, `LOWER`, `TRIM`, `CONTAINS`, `STARTSWITH`, `ENDSWITH`, `REPLACE`, `SPLIT`, `FIND`; join with `+` |
| Number | `ROUND`, `ABS`, `CEILING`, `FLOOR`, `SQRT`, `POWER`, `%` |
| Conversion | `STR`, `INT`, `FLOAT`, `DATE` |
| Aggregate | `SUM`, `AVG`, `MEDIAN`, `COUNT`, `COUNTD`, `MIN`, `MAX`, `ATTR` |

| Example | Formula |
| --- | --- |
| Profit ratio | `SUM([Profit]) / SUM([Sales])` (aggregate before dividing) |
| Days to ship | `DATEDIFF('day', [Order Date], [Ship Date])` |
| Email domain | `SPLIT([Email], "@", 2)` |
| Label | `IF [Sales] > 500 THEN "Large" ELSE "Small" END` |
| Comment | `// text after two slashes is ignored` |

“Cannot mix aggregate and non-aggregate arguments” means a row-level field was combined with an aggregated one, e.g. `[Sales] - SUM([Profit])`.

## Parameters

| | Parameter | Filter |
| --- | --- | --- |
| Values | One value | One or many |
| Tied to a field | No | Yes |
| Works on its own | No, must be referenced | Yes |
| Used in | Calculations, reference lines, Top N, bins, filters | Removing data from the view |
| Data types | Float, Integer, String, Boolean, Date, Date & Time | Any field |
| Allowable values | All, List, Range | Depends on the field |
| Controls | Type in, Slider, Single value list, Compact list | List, drop-down, slider, wildcard |

| When to use a parameter | How |
| --- | --- |
| Viewer chooses Top N | Integer parameter in the filter's Top tab |
| Viewer chooses the measure | String parameter + CASE calculation |
| What-if target or rate | Parameter used in a reference line or calculation |
| Click a mark to set it | Parameter action (Change Parameter) |
| Keep a list up to date | List > When workbook opens > Add values from a field |

---

# 3 · Sharing insights (25%)

## Formatting

| Field on Color | Legend | Palette |
| --- | --- | --- |
| Discrete dimension | One colour per value | Categorical |
| Continuous measure | Gradient | Sequential or diverging |

| Task | Menu path |
| --- | --- |
| Edit colours | Color > Edit Colors… (palette, stepped, reversed, full range, start/end/centre) |
| Opacity, border, halo | Color button |
| Shapes | Mark type Shape, dimension on Shape > Edit Shape… |
| Mark size | Size slider, or a measure on Size |
| Animations | Format > Animations… (on/off, duration, simultaneous or sequential) |
| Workbook fonts | Format > Workbook… |
| Sheet fonts | Format > Font… |
| Borders, shading, lines | Format menu, or right-click > Format… |
| Number format in one view | Right-click the pill > Format… |
| Show a hidden legend | Analysis > Legends, or Worksheet > Show Cards |
| Hide a legend | Legend menu > Hide Card |
| Title and caption | Worksheet > Show Title / Show Caption |
| Labels | Label > Show mark labels; All, Min/Max, Line Ends, Selected, Highlighted |
| Annotations | Right-click a mark > Annotate > Mark, Point or Area |
| Tooltip | Tooltip button; Insert > Sheets for a viz in tooltip |

## Dashboards and layout

| | Tiled | Floating |
| --- | --- | --- |
| Position | In a grid; objects don't overlap | Anywhere, can sit on top of others |
| Resizing | Adjusts with the dashboard | Fixed position and size |
| Switch | Hold **Shift** while dragging | Hold **Shift** while dragging |

| Size option | Behaviour |
| --- | --- |
| Fixed size | Always the same width and height (e.g. Desktop Browser 1000 × 800) |
| Automatic | Fills the window |
| Range | Between a minimum and maximum size |

| Object | Does |
| --- | --- |
| Horizontal / Vertical container | Groups items in a row or column |
| Text, Image, Blank | Content and spacing |
| Web Page | Shows a web page (also a target for URL actions) |
| Navigation | Button that opens another sheet |
| Download | Export button |
| Extension | Third-party add-in |

| Task | How |
| --- | --- |
| Add a sheet | Drag it from the Sheets list |
| Show a filter or parameter | Sheet menu > Filters / Parameters |
| Show/hide part of a dashboard | Container menu > Add Show/Hide Button |
| Position, size, border, padding | Layout pane (also shows the item hierarchy) |
| Phone and tablet versions | Device Preview > Add Layout (a phone layout is created by default) |
| Dashboard title | Dashboard > Show Title |
| Make a sheet fill its space | Sheet menu > Fit > Entire View |

## Actions and interactivity

| Action | What it does |
| --- | --- |
| Filter | Filters other sheets based on the selection |
| Highlight | Highlights related marks in other sheets, without removing data |
| Go to URL | Opens a web page, with field values in the URL |
| Go to Sheet | Opens another sheet, dashboard or story |
| Change Parameter | Sets a parameter's value from the selection |
| Change Set Values | Updates a set's members from the selection |

Run on: **Hover**, **Select**, **Menu**. When a filter selection is cleared: **Keep filtered values**, **Show all values**, **Exclude all values**. Create actions in Dashboard (or Worksheet) > **Actions…**; the quickest filter action is the **Use as Filter** icon.

| Interactive element for viewers | How to add it |
| --- | --- |
| Filter card | Right-click the filter > Show Filter (dashboard: sheet menu > Filters) |
| Data highlighter | Right-click a dimension > Show Highlighter (dashboard: sheet menu > Highlighters) |
| Tooltip | Tooltip button on the Marks card |
| Viz in tooltip | Tooltip editor > Insert > Sheets |

## Stories

| Task | How |
| --- | --- |
| New story | Story > New Story |
| Add a point | Drag a sheet or dashboard in; Blank or Duplicate for the next point |
| Keep changes | Update (overwrite) or Save as New (keep both); Revert undoes |
| Add text | The point's caption, or a Description box |
| Size | Story pane > Size |
| Navigator styles | Caption boxes, Numbers, Dots, Arrows only |

A dashboard shows several views at once; a story shows views one after another.

## Sharing and exporting

| Goal | Menu path | Result |
| --- | --- | --- |
| Packaged workbook | File > Save As > .twbx, or File > Export Packaged Workbook | Workbook with data |
| Image | Worksheet > Export > Image / Dashboard > Export Image | PNG, JPEG, BMP, EMF |
| PDF | File > Print to PDF | Entire workbook, active sheet or selected sheets |
| PowerPoint | File > Export As PowerPoint | One image per slide |
| Data | Worksheet > Export > Data | Access or CSV |
| Excel | Worksheet > Export > Crosstab to Excel | Excel table of the view |
| Copy | Worksheet > Copy > Data / Crosstab / Image | Clipboard |
| Underlying rows | Select marks > View Data, or Analysis > View Data | Summary tab, plus a tab per table (Full Data for one table); Download gives a CSV |
| Crosstab of a view | Worksheet > Duplicate as Crosstab | A new text-table sheet |
| Tableau Server / Cloud | Server > Publish Workbook (or Publish Data Source) | Online workbook with permissions |
| Tableau Public | Save to Tableau Public | Public on the internet; data must be an extract |
| View without editing | Tableau Reader | Opens .twbx files |

---

# 4 · Understanding Tableau concepts (15%)

## Dimensions and measures

| | Dimension | Measure |
| --- | --- | --- |
| Contains | Qualitative values: names, categories, dates, places, IDs | Quantitative, numeric values |
| In the view | Creates headers and sets the level of detail | Creates an axis and gets aggregated (SUM by default) |
| Examples | Region, Category, Order Date, Customer Name | Sales, Profit, Quantity, Discount |
| Watch out | Postal Code and Order ID are numbers but should be dimensions | |

Measure Names and Measure Values hold several measures in one field, for crosstabs and combined axes.

## Discrete and continuous

| | Discrete | Continuous |
| --- | --- | --- |
| Pill colour | Blue | Green |
| On Rows or Columns | Headers | Axis |
| On Color | Categorical palette | Gradient |
| As a filter | List of values | Range slider |
| Dates | Date parts (YEAR, MONTH…); all Januaries combined | Date values on a timeline; each January separate |

Pill colour shows discrete vs continuous, **not** dimension vs measure. Switch with right-click > Discrete / Continuous.

## Aggregation and level of detail

| Aggregation | Returns |
| --- | --- |
| SUM | Total (the default) |
| AVG | Mean |
| MEDIAN | Middle value |
| COUNT | Number of non-null values |
| COUNTD | Number of distinct values |
| MIN / MAX | Smallest / largest value |
| Percentile, Std. Dev, Variance | Spread of the values |
| ATTR | The value if all rows are the same, otherwise `*` |

| View | Marks | Each mark aggregates |
| --- | --- | --- |
| SUM(Sales), no dimensions | 1 | All rows |
| SUM(Sales) by Region (4) | 4 | One region's rows |
| By Region (4) and Segment (3) on Color | 12 | One region and segment |
| Aggregate Measures turned off | One per row | One row |

Adding a dimension to the view creates more marks, and each mark aggregates fewer rows. Dimensions only on the Filters shelf don't change the level of detail.

---

# Practice

## Common exam scenarios

| Scenario | Answer |
| --- | --- |
| A colleague opens your `.twb` and sees no data | Send a packaged workbook (`.twbx`) |
| A slow database, data changes once a day | Use an extract and refresh it daily |
| Join to a table at another level of detail inflates totals | Use a relationship |
| Keep customers who never ordered | Left join from Customers (or a relationship) |
| Show “NY” as “New York” everywhere | Alias |
| Postal Code is summed into one big number | Convert to Dimension, add a geographic role |
| Top 10 plus a Region filter shows fewer than 10 | Add the Region filter to context |
| One filter for every sheet on the same source | Apply to Worksheets > All Using This Data Source |
| Always show the last 12 months | Relative date filter |
| Seasonality across years | Discrete MONTH on Columns, YEAR on Color |
| Sales as bars and Profit Ratio as a line | Dual axis |
| Two measures with the same units on one axis | Combined axis |
| Combine two categories without changing the data | Group |
| Colour the top 20 customers, updating with data | Computed set (Top tab) on Color |
| Percent of Total shows 100% everywhere | Change Compute Using |
| How many orders fall in each 100 USD range | Bins of size 100 + histogram |
| Viewer changes a target line from a drop-down | Parameter + reference line |
| Viewer picks which measure a chart shows | String parameter + CASE calculation |
| Click a map region to filter a bar chart | Filter action on Select |
| Hover to make a category stand out everywhere | Highlight action on Hover |
| The dashboard must look the same on every screen | Fixed size |
| Rows behind a bar, in Excel | View Data > Download, or Export > Crosstab to Excel |
| All dashboards in one printable file | File > Print to PDF > Entire workbook |
