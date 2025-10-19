# SNP Detection using the Smith-Waterman Alignment Algorithm

## What is an SNP? And why is it important?

An SNP is a Single Nucleotide Polymorphism which is a variation at a single nucleotide (A, C, T, or G) at a specific location in a DNA Sequence. SNPs occur in people's DNA once in every 1,000 or so nucleotides. This means that it occurs very frequently in a human, usually with 4 to 5 million in the DNA. Being able to detect SNPs are important because they are used to be able to locate genes that are able to detect diseases.

## Using an FPGA for SNP Detection

The benefits of using an FPGA for SNP Detection is the low latency that an FPGA has which enables real-time detection of SNPs. There is also the benefit of using less power and less resources since an algorithm implementation for an FPGA is designed at the hardware level. Another benefit would be the parallelism of an FPGA which allows for multiple tasks to be completed concurrently, allowing for faster processing.

## Using a Small SNP Dataset vs. Generating Random SNP Data

For this project I would like to use a small genome dataset to show how the implementation of the Smith-Waterman alignment algorithm can be used for real-life purposes. The problem is I need to find a dataset for small genome sequences which consists of either taking a sample of a very large dataset or finding a dataset that has already been preprocessed for my purposes.

Another thing I could do is to generate random SNP data by having my Python script do that in a Jupyter Notebook. You can just rerun the cells every time you want to generate new data which makes it easier for me to test my code.

I might just try doing both for the sake of testing which one is better or not.

## Understanding the Smith-Waterman Algorithm

The Smith-Waterman Algorithm is an alignment algorithm that computes the local alignment of two genetic sequences. A local alignment of a sequence is just a subsection of an entire sequence, if I wanted to align the whole sequence I would use a global alignment algorithm such as the Needleman-Wusch algorithm. The local alignment of a sequence is used when there are regions of high similarity between 2 sequences. Potentially, outside of those regions, there are gaps and dissimilarities between the sequences.

For my purposes, I would have a reference sequence and a loop that would go through the comparisons, save the data, and get the similarity score to the reference. This is how the Smith-Waterman Algorithm works mathematically. It uses a recurrence relation to traverse a matrix (both sequences are at the side) and fills it with 2 for a match, -1 for a mismatch, and -2 for a gap between the sequences. The 0th row and 0th column of the matrix are filled with zeroes. You then go through the recursion function and fill out the matrix with the maximum number from the function.

This will give you a scoring matrix. To traceback the optimal alignment you have to get the
maximum number from the matrix and traceback based on the number that got you the
maximum score. The traceback will end once you reach 0.