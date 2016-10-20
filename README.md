# Wisdom Builder

PoC of a JavaScript Language Model Generator. Fetches repositories from GitHub to build a n-gram model of JavaScript tokens.

## Organization

Call the scripts in order. Each step fetches or transforms the data one step further.

## SETUP

- Make sure Ruby 2.x is installed
- `gem install whirly`

## PHASE 1 | Get List of Repositories from GitHub

Will create a text file containing the repositories to be fetched.

### Command

```
./phase1
```

### Data

--> data/1/reposistories.txt

## PHASE 2 | Download Repositories

Will clone all repositories from PHASE 1 and store them in one folder.

### Command

```
./phase2
```

### Data

--> data/2/<gh-user>/<repo_name>

## PHASE 3 | Flatten Files

Will extract all `.js`, `.jsx`, `.es6`, and `.jsm` files from the PHASE 2 data. It copies these files flatly to a new folder, but using random uuids as filenames.

### Command

```
./phase3
```

### Data

--> data/3/*.js

## PHASE 4 | Sort Out, Parse, Pre-Process

It removes comments, normalizes whitespace (replaces `\s` with ` `), and parses content of files into tokens, separated by single spaces.

### Command

```
./phase4
```

### Data

--> data/4/*

## PHASE 5 | Package Corpus File

For better portability, concatinate all single files into one huge file.

### Command

```
./phase5
```

### Data

--> data/5/javascript.corpus.bz2

## PHASE 6 | Build Language Model files

### Command

```
./phase6
```

### Data

--> data/6/javascript.arpa
--> data/6/javascript.model
--> data/6/javascript.vocab
--> data/6/javascript.candidates
--> data/6/javascript.candidates.vocab

## Consume Corpus

See

- https://github.com/wisdom-query
- https://github.com/atom-wisdom

## License

Copyright (C) 2016 Jan Lelis, http://janlelis.com. Released under the MIT license.

KenLM is by Kenneth Heafield and licensed under the LGPLv2 license. See kenlm/LICENSE for more details.
