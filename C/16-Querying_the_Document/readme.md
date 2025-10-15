# Document Parser in C

## Medium

### Objective

The objective of this challenge is to process a document of text that is structured into paragraphs, sentences, and words. You need to read the document, parse it into a hierarchical data structure, and then handle several queries to retrieve a specific word, sentence, or paragraph based on its index.

The core of the challenge lies in dynamically allocating memory to store the document. Since the number of paragraphs, sentences per paragraph, and words per sentence are not known beforehand, you must use functions like `malloc` and `realloc` to adjust memory on the fly.

### Data Structures

The entire document is stored in a dynamically allocated four-dimensional character array (`char****`).

* `char**** document`: Represents the entire document. It's an array of paragraphs.
    * `document[i]`: Represents the `i`-th paragraph. It's an array of sentences (`char***`).
        * `document[i][j]`: Represents the `j`-th sentence in the `i`-th paragraph. It's an array of words (`char**`).
            * `document[i][j][k]`: Represents the `k`-th word in the `j`-th sentence of the `i`-th paragraph. It's a string (`char*`).

### Input Format

* The first line contains an integer `n`, the total number of paragraphs.
* The next `n` lines contain the text of each paragraph. Paragraphs are separated by newlines (`\n`), sentences by periods (`.`), and words by spaces (` `).
* The next line contains an integer `q`, the total number of queries.
* Each of the following `q` lines contains a query in one of the three specified formats:
    * `1 k` : Retrieve the `k`-th paragraph.
    * `2 k m` : Retrieve the `k`-th sentence of the `m`-th paragraph.
    * `3 k m n` : Retrieve the `k`-th word of the `m`-th sentence of the `n`-th paragraph.

### Output Format

For each query, the program will print the requested word, sentence, or paragraph to standard output, followed by a newline. The printing logic is handled by the provided `print_word`, `print_sentence`, and `print_paragraph` functions.

### Sample Input

2
Learning C is fun. Followed by pointers.
This is the second paragraph.
3
3 1 1 1
2 1 2
1 1

### Sample Output

Learning
This is the second paragraph
Learning C is fun.Followed by pointers.