# Tableau Reference Tables

The key comparison tables for the Tableau Desktop Foundations exam, collected in one place and grouped by exam domain. The exam is closed-book, so these are worth knowing by heart.

## Domain 1: Connecting to and preparing data

### Live connection vs extract

| | Live connection | Extract |
| --- | --- | --- |
| Where the data is | Stays in the source; Tableau queries it every time the view changes | A compressed snapshot saved in a `.hyper` file |
| How current | Always up to date | Only as current as the last refresh |
| Speed | Depends on the database | Usually fast |
| Works offline | No | Yes |
| Best when | You need real-time data, the database is fast, or data can't be copied out | The source is slow, you work offline, you need a subset, or you publish to Tableau Public |
| How to set it | Data Source page > **Live** | Data Source page > **Extract**, or Data > *source* > **Extract Data…** |

### Extract refresh types

| Refresh | What it does |
| --- | --- |
| Full | Replaces all data in the extract |
| Incremental | Adds only new rows, based on a column that increases (date or ID); doesn't update changed or deleted rows |

### Tableau file types

| Extension | Name | Contains data? | Use it to |
| --- | --- | --- | --- |
| `.twb` | Workbook | No, only a link to the source | Share with people who can reach the same data |
| `.twbx` | Packaged workbook | Yes: extracts, local files, images | Share with anyone, open in Tableau Reader |
| `.tds` | Data source | No, connection info and metadata | Reuse calculated fields, aliases, groups and default properties |
| `.tdsx` | Packaged data source | Yes | Reuse a data source with its local data |
| `.hyper` | Extract | Yes | Store extract data (older versions used `.tde`) |
| `.tbm` | Bookmark | Depends | Copy one worksheet into another workbook |

### Ways to combine data

| Method | Layer | Result | Choose it when |
| --- | --- | --- | --- |
| Relationship | Logical | Tables stay separate; Tableau picks the join at query time | Default choice; tables at different levels of detail |
| Join | Physical | Columns added side by side on a key | You need control of the join type, or one flat table |
| Union | Physical | Rows stacked on top of each other | Tables have the same columns (e.g. one sheet per year) |
| Blend | Worksheet | Secondary source aggregated, then combined like a left join | Two separate data sources, set up per sheet |

### Join types

| Join | Keeps |
| --- | --- |
| Inner | Only rows that match in both tables |
| Left | All rows from the left table, plus matches from the right (no match = null) |
| Right | All rows from the right table, plus matches from the left |
| Full outer | All rows from both tables |

### Data types and icons

| Data type | Icon |
| --- | --- |
| String | Abc |
| Number (decimal / whole) | # |
| Date | Calendar |
| Date & Time | Calendar with clock |
| Boolean | T\|F |
| Geographic | Globe |

### Default properties

| Field type | Properties you can set |
| --- | --- |
| Dimension | Comment, Color, Shape, Sort, Aliases |
| Measure | Comment, Color, Number Format, Aggregation, Total Using |
| Date | Date Format, Fiscal Year Start (plus the dimension properties) |

## Domain 2: Exploring and analyzing data

### Basic charts

| Chart | How to build it | Show Me needs |
| --- | --- | --- |
| Bar | Dimension on Rows, measure on Columns | 0+ dimensions, 1+ measures |
| Stacked bar | Bar chart + a dimension on Color | 1+ dimensions, 1+ measures |
| Line | Date on Columns, measure on Rows | 1 date, 0+ dimensions, 1+ measures |
| Scatter plot | Measure on Rows and measure on Columns; dimension on Detail | 0+ dimensions, 2–4 measures |
| Symbol map | Double-click a geographic field; measure on Size | 1 geo dimension, 0–2 measures |
| Filled map | Marks type Map; measure on Color | 1 geo dimension, 0–1 measure |
| Density map | Marks type Density | Many overlapping points |
| Text table | Dimensions on Rows and Columns, measure on Text | 1+ dimensions, 1+ measures |
| Highlight table | Text table + measure on Color, marks type Square | 1+ dimensions, 1 measure |
| Treemap | Dimension on Detail/Label, measure on Size and Color | 1+ dimensions, 1–2 measures |
| Pie | Marks type Pie; dimension on Color, measure on Angle | 1+ dimensions, 1–2 measures |
| Histogram | Bins of one measure on Columns, count on Rows | 1 measure |
| Dual axis | Two measures, right-click the second > Dual Axis | 1 date, 2 measures (dual line / combination) |
| Bullet graph | Actual as bar, target as reference line | 0+ dimensions, 2 measures |

### Dual axis vs combined axis

| | Dual axis | Combined (shared) axis |
| --- | --- | --- |
| Axes | Two: left and right | One |
| Marks cards | One per measure | One |
| Mark types | Can differ (bar + line) | Same for both |
| How | Right-click the second pill > **Dual Axis** | Drag the second measure onto the existing axis |
| Fields used | The two measures | Measure Names + Measure Values |

### Groups vs sets

| | Group | Set |
| --- | --- | --- |
| What it does | Combines members into new categories | Splits members into In and Out |
| Values | As many as you make (+ optional "Other") | Two: In / Out |
| Dynamic? | No | Yes, if computed by condition or Top N |
| Icon | Paperclip | Venn diagram |
| Create from | Data pane, headers, or marks | Data pane, or selected marks |

### Filters

| Filter | Where you create it | Notes |
| --- | --- | --- |
| Extract | Extract dialog | Limits rows in the extract |
| Data source | Data Source page > Filters | Applies to all sheets using the source |
| Context | Right-click a filter > **Add to Context** | Grey pill; runs before Top N and FIXED |
| Dimension | Filters shelf | Tabs: General, Wildcard, Condition, Top |
| Measure | Filters shelf | Range, At least, At most, Special |
| Date | Filters shelf | Relative date, Range of dates, date parts, Individual dates |
| Table calculation | Filters shelf with a table calc | Runs last; only hides marks |

### Order of operations

| Step | What runs |
| --- | --- |
| 1 | Extract filters |
| 2 | Data source filters |
| 3 | Context filters |
| 4 | Sets, conditional and Top N filters, FIXED LOD expressions |
| 5 | Dimension filters |
| 6 | Data blending, INCLUDE and EXCLUDE LOD expressions |
| 7 | Measure filters |
| 8 | Forecasts, table calculations, totals |
| 9 | Table calculation filters |

### Analytics pane

| Section | Items |
| --- | --- |
| Summarize | Constant Line, Average Line, Median with Quartiles, Box Plot, Totals |
| Model | Average with 95% CI, Median with 95% CI, Trend Line, Forecast, Cluster |
| Custom | Reference Line, Reference Band, Distribution Band, Box Plot |

### Reference lines, bands and distributions

| Item | Shows | Example |
| --- | --- | --- |
| Reference line | One value | Average sales |
| Reference band | Shaded area between two values | Between min and max |
| Distribution band | Shaded ranges from a distribution | 60% and 80% of average, percentiles, standard deviations |

Scope options: **Entire Table**, **Per Pane**, **Per Cell**.

### Quick table calculations

| Calculation | Answers |
| --- | --- |
| Running Total | What is the cumulative total so far? |
| Difference | How much did it change from the previous value? |
| Percent Difference | By what % did it change from the previous value? |
| Percent of Total | What share of the total is this mark? |
| Rank | Where does this mark rank? |
| Percentile | What percentile is this mark in? |
| Moving Average | What is the average of the last few values? |
| YTD Total | What is the total so far this year? |
| Compound Growth Rate | What is the average growth rate per period? |
| Year over Year Growth | How much did it grow compared with the same period last year? |
| YTD Growth | How does year-to-date compare with last year's year-to-date? |

### Date functions

| Function | Returns | Example result |
| --- | --- | --- |
| `DATEPART('month', [Order Date])` | Integer | 3 |
| `DATENAME('month', [Order Date])` | String | March |
| `DATETRUNC('month', [Order Date])` | Date | 1 March 2025 |
| `DATEDIFF('day', [Order Date], [Ship Date])` | Integer | 4 |
| `DATEADD('month', 3, [Order Date])` | Date | 3 months later |
| `TODAY()` / `NOW()` | Date / Date & Time | Current date / date and time |

### Logical and null functions

| Function | Use |
| --- | --- |
| `IF … THEN … ELSEIF … ELSE … END` | Several conditions |
| `IIF(test, then, else)` | Short IF |
| `CASE [field] WHEN … THEN … END` | Compare one field to values |
| `IFNULL([x], 0)` | Replace null with a value |
| `ZN([x])` | Replace null with zero |
| `ISNULL([x])` | TRUE if null |

### Parameter vs filter

| | Parameter | Filter |
| --- | --- | --- |
| Values | One value | One or many |
| Tied to a field | No | Yes |
| Works on its own | No, must be referenced | Yes |
| Used in | Calculations, reference lines, Top N, bins, filters | Removing data from the view |
| Data types | Float, Integer, String, Boolean, Date, Date & Time | Any field |
| Allowable values | All, List, Range | Depends on the field |

## Domain 3: Sharing insights

### Colour on the Marks card

| Field on Color | Legend | Palette |
| --- | --- | --- |
| Discrete dimension | One colour per member | Categorical |
| Continuous measure | Gradient | Sequential or diverging |

### Tiled vs floating

| | Tiled | Floating |
| --- | --- | --- |
| Position | In a grid; objects don't overlap | Anywhere, can sit on top of others |
| Resizing | Adjusts with the dashboard | Fixed position and size |
| Switch | Hold **Shift** while dragging | Hold **Shift** while dragging |

### Dashboard size

| Option | Behaviour |
| --- | --- |
| Fixed size | Always the same width and height |
| Automatic | Fills the window |
| Range | Between a minimum and maximum size |

### Dashboard actions

| Action | What it does |
| --- | --- |
| Filter | Filters other sheets based on the selection |
| Highlight | Highlights related marks in other sheets |
| Go to URL | Opens a web page, with field values in the URL |
| Go to Sheet | Opens another sheet, dashboard or story |
| Change Parameter | Sets a parameter's value from the selection |
| Change Set Values | Updates a set's members from the selection |

Triggers: **Hover**, **Select**, **Menu**. When a filter selection is cleared: **Keep filtered values**, **Show all values**, **Exclude all values**.

### Exporting and sharing

| Goal | Menu path | Result |
| --- | --- | --- |
| Packaged workbook | File > Save As > .twbx, or File > Export Packaged Workbook | Workbook with data |
| Image | Worksheet > Export > Image / Dashboard > Export Image | PNG, JPEG, BMP, EMF |
| PDF | File > Print to PDF | Entire workbook, active sheet or selected sheets |
| PowerPoint | File > Export As PowerPoint | One image per slide |
| Data | Worksheet > Export > Data | Access or CSV |
| Excel | Worksheet > Export > Crosstab to Excel | Excel table of the view |
| Underlying rows | Right-click a mark > View Data | Summary and Full Data tabs |
| Tableau Server / Cloud | Server > Publish Workbook | Online workbook with permissions |
| Tableau Public | File > Save to Tableau Public | Public on the internet; data must be an extract |

## Domain 4: Understanding Tableau concepts

### Dimensions vs measures

| | Dimension | Measure |
| --- | --- | --- |
| Contains | Qualitative values: names, categories, dates, places | Quantitative, numeric values |
| In the view | Creates headers and sets the level of detail | Gets aggregated (SUM by default) |
| Examples | Region, Category, Order Date, Customer Name | Sales, Profit, Quantity, Discount |

### Discrete vs continuous

| | Discrete | Continuous |
| --- | --- | --- |
| Pill colour | Blue | Green |
| On Rows or Columns | Headers | Axis |
| On Color | Categorical palette | Gradient |
| As a filter | List of values | Range slider |
| Dates | Date parts (YEAR, MONTH…); all Januaries combined | Date values on a timeline; each January separate |

Pill colour shows discrete vs continuous, **not** dimension vs measure.

### Aggregations

| Aggregation | Returns |
| --- | --- |
| SUM | Total (the default) |
| AVG | Mean |
| MEDIAN | Middle value |
| COUNT | Number of non-null values |
| COUNTD | Number of distinct values |
| MIN / MAX | Smallest / largest value |
| ATTR | The value if all rows are the same, otherwise an asterisk |

Adding a dimension to the view creates more marks, and each mark aggregates fewer rows. Dimensions only on the Filters shelf don't change the level of detail.
