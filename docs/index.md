## SpikeForest documentation

SpikeForest is an open-source benchmarking website for spike sorting algorithms. The front end is [under development here](https://github.com/elovero/spike-front).

You can view these docs either on the [hosted website](https://users.flatironinstitute.org/~magland/docs/) or on the [github repo](https://github.com/magland/docs/blob/master/docs/index.md).

[Overview of the system](overview.md) -- in progress

## Overview notebooks

* [Overview of SpikeInterface, SpikeWidgets, and SpikeToolkit](https://gist.github.com/magland/e43542fe2dfe856fd04903b9ff1f8e4e) -- [live notebook](https://colab.research.google.com/gist/magland/e43542fe2dfe856fd04903b9ff1f8e4e)
* [Running MountainSort directly from python](https://gist.github.com/magland/ee686398228a16adf8b95af4edde096b) -- [live notebook](https://colab.research.google.com/gist/magland/ee686398228a16adf8b95af4edde096b)
* [Overview of KBucket and SpikeForest](https://gist.github.com/magland/318c7bc43df9dd528f667589eaa2482d) -- [live notebook](https://colab.research.google.com/gist/magland/318c7bc43df9dd528f667589eaa2482d)

## Assembling the recordings and studies

The following notebook is used to assemble the recordings and studies that populate the website and to provide the input to the batch processing: https://colab.research.google.com/gist/magland/4b97b837c594469e48b405066aa5bca5/prepare_studies.ipynb

## Batch processing

Since processing loads data from kbucket and saves data back to kbucket, it can be performed on any computer. The scripts are written such that parallelization is achieved by running the same script simultaneously on many different cores / compute nodes. The pairio database is used to coordinate the jobs so that each script will perform different sorting jobs. The current scripts used for processing [are found here](https://github.com/magland/spikeforest/tree/master/spikeforest/sf_batch). The documentation for these scripts is in the process of being assembled [TODO].

## Exploring processing results

The sorting results of SpikeForest can be inspected from any python notebook using the SpikeForest python API. An example of using this API [in this live notebook](https://colab.research.google.com/gist/magland/1028fc92568c86f6b5a6e56766f9a8f1/explore_spikeforest_results.ipynb), and the [corresponding gist](https://gist.github.com/magland/1028fc92568c86f6b5a6e56766f9a8f1#file-explore_spikeforest_results-ipynb).

The source code for [this API is here](https://github.com/magland/spikeforest/blob/master/spikeforest/sfdata/sfdata.py) (TODO: document this API).

## SpikeForest processing notebooks

**Note: This section needs to be revised -- the pipeline has been overhauled -- docs are being assembled above**

* Step 1: [Assemble the studies and datasets](https://gist.github.com/magland/4b97b837c594469e48b405066aa5bca5) -- [live notebook](https://colab.research.google.com/gist/magland/4b97b837c594469e48b405066aa5bca5/prepare_studies.ipynb)
* Step 2: [Process the datasets](https://gist.github.com/magland/9d9d1a0a58aa694d5c2e71e3717dd1ef#file-notebook-ipynb) -- [live notebook](https://colab.research.google.com/gist/magland/9d9d1a0a58aa694d5c2e71e3717dd1ef) -- updated 3 Nov 2018 -- see docs on the .ipynb discussing parallelization
* Step 3: [Sort the datasets](https://gist.github.com/magland/3ba2b1fe6ff138deba0edaedb5de5867#file-notebook-ipynb) -- [live notebook](https://colab.research.google.com/gist/magland/3ba2b1fe6ff138deba0edaedb5de5867) -- added 6 Nov 2018
* Step 4: Process sorting results
* Step 5: Compare with ground truth

## Loading data from JavaScript

**TODO: this section needs to be expanded to describe how to load spike sorting results**

* [Load SpikeForest studies and datasets in JavaScript](https://codesandbox.io/s/w7pp32vo0w) -- [The live web page](https://w7pp32vo0w.codesandbox.io/) -- updated 6 Nov 2018 -- now contains a unit waveforms image.

## Meeting notes

* [Meeting notes](meeting_notes.md)

## Misc links:

* [MountainSort](mountainsort.md)
* [MountainLab](mountainlab.md)
* [KBucket](kbucket.md)
* [SpikeForest python package](https://github.com/magland/spikeforest)



## More technical info

* [KBucket technical info](https://gist.github.com/magland/fb2a879975f6e1d44cc624297c1b6656#file-kbucket_technical_info-ipynb) -- [live notebook](https://colab.research.google.com/gist/magland/fb2a879975f6e1d44cc624297c1b6656)
