# ID2S_FINAL - Book recommendation system

# Data collection

- Scrape tags and metadata (book title, author, ratings, download counts,...) of 10,000 English books.

- Extract `.html`, `.txt`, `.tex` files from crawled `.zip` files (crawled by NQThinh, with 50% of files being uploaded on 8/12, and the rest 50% of files being uploaded on 9/12). Images files (`.png`, `.jpg`) will not be included.

# Data cleaning & Wrangling

## Preparing the data

- NQThinh
  - Do [EDA](https://www.geeksforgeeks.org/what-is-exploratory-data-analysis/) 
  - Only include tags that have **5** associated books at minimum.

- Split compound tags into smaller tags automatically and manually, e.g., -->  
  + **"History -- 1932"** &rarr; **"History"**, **"1932"** --> __TNguyen__

  + **"Sci-fi"**, **"SF"** --> 
   &rarr; **"Science Fiction"** [Top 50, 100, 200] --> __QVuong__

- Check tags/books for profanity or illegal content. [Top 200, 500] --> __MQuang__

## Finding simple patterns --> __TDThinh__

- Do simple rankings of tags: 
  + By amount of books in tags
  + By amount of tag connections
  + By download count of all books in tags [TBD]
  + By average ratings of all books in tags [TBD]

- Show tags trend:
  + By year
  + By season

- **[Optional]** Recognizing other patterns.

# Data Analysis

## Create a tag network to create the book indexer

- Pair up all qualified tags. E.g. **(Science Fiction, Romance)**, **(History, 1936)**.

- Create a graph from the collected data using the `networkx` library

- Using heurisic (a combination of book count, tag popularity and tags relation) to decide the parent-child relation between each node &rarr; The resulted tree is the **ideal book indexer**

## Create a basic book recommendation system

- Build a book-tag matrix (book as rows, tags as columns), with 1 being the book has the tag, and 0 otherwise

- Apply similarity measures (cosine, Jaccard) to create a **basic book recommendation system**.

- Favor newer books
