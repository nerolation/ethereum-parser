# Ethereum Parser

## Description
This is an open-source Ethereum blockchain parser designed to work with various layers of the Ethereum blockchain, including the Execution layer, Consensus layer, MEVBoost, and Contract Events (Application layer). It provides a comprehensive set of features for parsing and analyzing Ethereum data, and supports saving to BigQuery or SQL databases.

## Installation
Clone the repository and install the required packages:
```bash
git clone https://github.com/yourusername/Ethereum-Parser.git
cd Ethereum-Parser
pip install -r requirements.txt
```

## Usage

### Execution Layer
To run the Execution layer parser, use the following command:
```bash
python parser.py exec [arguments]
```
Arguments:
- `-bf, --back-fill`: Backfilling from the first block known backwards.
- `-cg, --close-gaps`: Parse with closing gaps.
- `-ul, --update-locally`: Load latest block from BigQuery and update locally.
- `-up, --update-bq-with-local`: Update BigQuery tables with local progress.
- `-down, --update-local-with-bq`: Update Local tables with BigQuery progress.
- `-m, --saving-mode`: Saving mode (`bq` or `sql`).
- `-t, --tasks`: Number of concurrent tasks to start.

### Consensus Layer
To run the Consensus layer parser, use the following command:
```bash
python parser.py cl [arguments]
```
Arguments:
- `-l, --blockprint-data-location`: The location of the blockprint data.
- `-bf, --back-fill`: Backfilling from the first slot known backwards.
- `-hl, --heal-missed-slots`: Update proposers for missed slots after parsing.
- `-up, --update-bq-with-local`: Update BigQuery tables with local progress.
- `-down, --update-local-with-bq`: Update Local tables with BigQuery progress.
- `-testing, --testing`: In testing mode, client classification is ignored and no saving.
- `-ul, --update-locally`: Retrieve latest block from BigQuery but do updates locally.
- `-t, --tasks`: Cores to use (only valid if `-mp` is set).
- `-kp, --keep-pace`: Keep pace with head.
- `-cg, --close-gaps`: Parse with closing gaps.
- `-m, --saving-mode`: Saving mode (`bq` or `sql`).

### MEVBoost
To run the MEVBoost parser, use the following command:
```bash
python parser.py mev [arguments]
```
Arguments:
- `setting`: Either parsing delivered payloads or received bids.
- `-bf, --back-fill`: Backfilling from the first block known backwards.
- `-cg, --close-gaps`: Parse with closing gaps.
- `-ul, --update-locally`: Load latest block from BigQuery and update locally.
- `-up, --update-bq-with-local`: Update BigQuery tables with local progress.
- `-down, --update-local-with-bq`: Update Local tables with BigQuery progress.
- `-m, --saving-mode`: Saving mode (`bq` or `sql`).

### Contract Events (Application Layer)
To run the Contract Events parser, use the following command:
```bash
python parser.py ev [arguments]
```
Arguments:
- `-up, --update-bq-with-local`: Update BigQuery tables with local progress.
- `-sb, --start-block`: Start Block for parsing (incl).
- `-eb, --end-block`: End Block for parsing (incl).

## Examples
Here are some example usages:

### Execution Layer
```bash
python parser.py el -bf -m sql
```

### Consensus Layer
```bash
python parser.py cl -l /path/to/blockprint/data -bf
```

### MEVBoost
```bash
python parser.py mev payloads -bf
```

### Contract Events
```bash
python parser.py event -sb 0 -eb 1000
```

