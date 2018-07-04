[![Build Status](https://travis-ci.org/jacobseiler/testing_tutorial.svg?branch=master)](https://travis-ci.org/jacobseiler/testing_tutorial)

# testing_tutorial

This repository aims to highlight the importance of testing code and provides instructions on setting up automated Travis testing.

# Why Test?

An important question that you should ask yourself is **How do I know my code is running correctly?** Whilst the answer to this question may often be **My code compiles and executes without raising an error** the reality is more subtle than this.  How can you be certain that your code, which could be potentially thousands of lines long, runs in an identical manner after **every** commit?

As you may have guessed, the answer is to create a suite of tests wherein you enter known input and check the output is **exactly** what you expect.

## What's in this Repo

This repository contains a small snippet of code (in the `src` directory) that we wish to test.  This snippet performs downsampling in which an input cubic grid (say size 128x128x128) is downsampled to a smaller grid (say size 64x64x64) whilst maintaining identical averages over each region.

The code is checked by the `tests.py` file in the `tests` directory.  This file performs two checks:
* Given a grid that contains all values of 1.0, the output grid should contain all values of 1.0. This is because the averages within it region is conversed.
* If the input grid is (e.g.,) 128x128x128 and the output grid is requested to be (e.g.,) 64x64x64, we check that given a grid where every 8th cell contains a value of 8.0, the output grid should contain all values of 1.0.  This is because we average over (128/64)^3 cells. 

These checks are run by invoking `python tests.py`.

# Automating Tests

Great, we've now ensured that our code produces the expected output for a specific set on of inputs.  However we want to ensure that any changes we make to the codebase does not break our pipeline.  Whilst we could run the tests every time we make a change, this can become cumbersome.  Furthermore, if we want other people to contribute to our code, we need to ensure that their contributions 
