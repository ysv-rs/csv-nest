# csv-unnest
Unnest values in CSV files.

**Note:** this repository is a stub, a proposal, an idea. Perhaps someday the idea will be implemented.

## Usage

`input.csv` file:

```csv
country,cities
United States,"New York,Atlanta,Los Angeles"
Germany,"Berlin"
Russia,"Moscow,Novosibirsk"
```

Command:

```shell
csvnest unnest --column cities --delimiter ',' < input.csv > output.csv
```

which writes to `output.csv` file:

```csv
country,cities
United States,New York
United States,Atlanta
United States,Los Angeles
Germany,Berlin
Russia,Moscow
Russia,Novosibirsk
```

It happens very often that a CSV file contains multiple values in a cell, separated with `,` as shown above, or a space, or a `|`. Unnesting means duplicating the row so that every copy contains one of the values that were previously nested.
