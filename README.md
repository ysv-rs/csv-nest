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
csvunnest --column cities --delimiter ',' < input.csv > output.csv
```

which writes the following to `output.csv` file:

```csv
country,cities
United States,New York
United States,Atlanta
United States,Los Angeles
Germany,Berlin
Russia,Moscow
Russia,Novosibirsk
```

## Motivation

It happens very often that a CSV file contains multiple values in a cell, separated with `,` as shown above, or a space, or a `|`. Unnesting means duplicating the row so that every copy contains one of the values that were previously nested.

This makes it possible to analyse the data with other CSV capable tools.

## Use cases

- Clean up incoming CSV data for better normalization
- Prepare reports by converting one CSV schema to another

## Technical requirements

*This section is transient and should materialize as a series of concrete tasks.*

- Should be written in Rust programming language.
- Must read the source file line by line, not fetching the whole file into RAM.
- For performance, reading and writing should happen in separate threads communicating via a queue with buffer.
- Possibly useful libraries: `csv` to read & write data, `clap` for command line arguments.
