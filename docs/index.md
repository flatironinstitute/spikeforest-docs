## SpikeForest documentation

SpikeForest is an open-source benchmarking website for spike sorting algorithms. The front end is [under development here](https://github.com/elovero/spike-front).

You can view these docs either on the [hosted website](https://users.flatironinstitute.org/~magland/spikeforest-docs/) or on the [github repo](https://github.com/flatironinstitute/spikeforest-docs/blob/master/docs/index.md).

## Updates of 12/17/2018

Here's the --help for the newest version of sf_run_batch:
```
> sf_run_batch --help
usage: sf_run_batch [-h] [--run_prefix RUN_PREFIX] [--clear]
                    [--mlpr_force_run] [--job_index JOB_INDEX]
                    [--parallel PARALLEL] [--repeat] [--delay DELAY]
                    [batch_names [batch_names ...]]

Run a spikeforest processing batch

positional arguments:
  batch_names           The names of the batches to run

optional arguments:
  -h, --help            show this help message and exit
  --run_prefix       Prefix to run command (e.g., srun -c 2 -n 40 -p ccm)
  --clear                First clear the jobs so that all jobs are run.
  --mlpr_force_run      Force run the MountainLab processors
  --job_index        Only run one job and do not assemble the results
  --parallel            Number of times to simultaneously do the run command (this is for a single workstation, not using srun).
  --repeat             Continuously repeat the processing with a delay between successive runs
  --delay DELAY         Number of seconds to delay between runs (to be used
```

The powerful combination is --run_prefix (for srun) and --repeat, with a collection of batch_names, because then it will continue checking for modifications to the batches and automatically rerun when needed. This enables launching of processing from the notebooks.

## Updates of 12/11/2018

All the server-side python code has been moved into a single meta repository. For now it is called [spikeforest2](https://github.com/flatironinstitute/spikeforest2), but will ultimately be renamed to "spikeforest". It contains a snapshot of a number of different dependent projects contained in repo/. These may or may not be up-to-date with the associated stand-alone packages. In this way, spikeforest2 is a snapshot project that contains all the necessary code, and is less susceptible to breaking changes in other packages.

The `sf_run_batch` and `sf_run_batch_command` programms are now available from the spikeforest2 repository above.

Some flags that are useful for testing have been added to sf_run_batch and sf_run_batch_command. These include --clear, --job_index, and --mlpr_force_run. More info is available by running

```
sf_run_batch --help
sf_run_batch_command --help
```

## Analysis

The SpikeForest analysis consists of preparing the studies and recordings, summarizing the recordings, running spike sorting, comparing with ground truth, and assembling all the results for the front-end (website). For now, all source code for performing these actions is contained in the [spikeforest2](https://github.com/flatironinstitute/spikeforest2) repository.

**Live notebooks (newer):**

* Main analysis: [spikeforest_analysis2.ipynb](https://colab.research.google.com/github/flatironinstitute/spikeforest-docs/blob/master/notebooks/spikeforest_analysis2.ipynb) or [on github](https://github.com/flatironinstitute/spikeforest-docs/blob/master/notebooks/spikeforest_analysis2.ipynb)


**Live notebooks (older):**

* Main analysis (see newer version above): [spikeforest_analysis.ipynb](https://colab.research.google.com/github/flatironinstitute/spikeforest-docs/blob/master/notebooks/spikeforest_analysis.ipynb) or [on github](https://github.com/flatironinstitute/spikeforest-docs/blob/master/notebooks/spikeforest_analysis.ipynb)
* Assemble data for the website: [assemble_website_data.ipynb](https://colab.research.google.com/github/flatironinstitute/spikeforest-docs/blob/master/notebooks/assemble_website_data.ipynb) or [on github](https://github.com/flatironinstitute/spikeforest-docs/blob/master/notebooks/assemble_website_data.ipynb)
* Browse recordings: [browse_recordings.ipynb](https://colab.research.google.com/github/flatironinstitute/spikeforest-docs/blob/master/notebooks/browse_recordings.ipynb)
* Monitor batches (work in progress): [monitor_batches.ipynb](https://colab.research.google.com/github/flatironinstitute/spikeforest-docs/blob/master/notebooks/monitor_batches.ipynb)

## Overview notebooks

* [Running MountainSort directly from python](https://gist.github.com/magland/ee686398228a16adf8b95af4edde096b) -- [live notebook](https://colab.research.google.com/gist/magland/ee686398228a16adf8b95af4edde096b)
* [Overview of KBucket and SpikeForest](https://gist.github.com/magland/318c7bc43df9dd528f667589eaa2482d) -- [live notebook](https://colab.research.google.com/gist/magland/318c7bc43df9dd528f667589eaa2482d)
* (OLD) [Overview of SpikeInterface, SpikeWidgets, and SpikeToolkit](https://gist.github.com/magland/e43542fe2dfe856fd04903b9ff1f8e4e) -- [live notebook](https://colab.research.google.com/gist/magland/e43542fe2dfe856fd04903b9ff1f8e4e)

## Configuring kbucket

**(Advanced)**

The following notebook shows how kbucket/pairio are configured (password protected, etc): [live notebook](https://colab.research.google.com/gist/magland/b4e675106063f0dd763b24c93d2ec395/kbucket_config.ipynb)

## Exploring studies and processing results

**Somewhat obsolete**

[Overview of the system](overview.md) -- in progress

The studies and sorting results of SpikeForest can be browsed/explored from any python notebook using the SpikeForest python API. An example of this is found in the below notebook.

* explore_spikeforest_results.ipynb -- [live notebook](https://colab.research.google.com/gist/magland/ec67d20c0a2c93ce2b6bc452d041783b/explore_spikeforest_results.ipynb) | [gist](https://gist.github.com/magland/ec67d20c0a2c93ce2b6bc452d041783b#file-explore_spikeforest_results-ipynb)

The source code for [this API is here](https://github.com/magland/spikeforest/blob/master/spikeforest/sfdata/sfdata.py) (TODO: document this API).

Here's a notebook for plotting accuracy vs SNR for various algorithms:

* sf_comparison_plots.ipynb -- [live notebook](https://colab.research.google.com/gist/magland/5c82306f20aa2a81ba9d429b5e1d3c23/sf_comparison_plots.ipynb) | [gist](https://gist.github.com/magland/5c82306f20aa2a81ba9d429b5e1d3c23#file-sf_comparison_plots-ipynb)



## Assembling the recordings and studies

**Obsolete -- see Analysis above**

The following notebook is used to assemble the recordings and studies that populate the website and to provide the input to the batch processing.

* prepare_studies.ipynb -- [live notebook](https://colab.research.google.com/gist/magland/4b97b837c594469e48b405066aa5bca5/prepare_studies.ipynb) | [gist](https://gist.github.com/magland/4b97b837c594469e48b405066aa5bca5)

## Batch processing

**Obsolete -- see Analysis above**

Processing is organized in batches that are stored on kbucket. An online notebook is used to assemble the batches. The batch processing can then be launched on any computer, for example a compute cluster. The scripts are written such that parallelization is achieved by running the same script simultaneously on many different cores / compute nodes. The pairio database is used to coordinate the jobs so that each script will perform different sorting jobs.

* sf_prepare_batches.ipynb -- [live notebook](https://colab.research.google.com/gist/magland/1a35e661f783aa97e4b31f67075fe12f/sf_prepare_batches.ipynb) | [gist](https://gist.github.com/magland/1a35e661f783aa97e4b31f67075fe12f) -- Defines the batches for processing

## Loading data from JavaScript

**NOTE: THIS SECTION IS MOSTLY OBSOLETE**

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

## Old stuff

### SpikeForest processing notebooks

**Note: This section needs to be revised -- the pipeline has been overhauled -- docs are being assembled above**

* Step 1: [Assemble the studies and datasets](https://gist.github.com/magland/4b97b837c594469e48b405066aa5bca5) -- [live notebook](https://colab.research.google.com/gist/magland/4b97b837c594469e48b405066aa5bca5/prepare_studies.ipynb)
* Step 2: [Process the datasets](https://gist.github.com/magland/9d9d1a0a58aa694d5c2e71e3717dd1ef#file-notebook-ipynb) -- [live notebook](https://colab.research.google.com/gist/magland/9d9d1a0a58aa694d5c2e71e3717dd1ef) -- updated 3 Nov 2018 -- see docs on the .ipynb discussing parallelization
* Step 3: [Sort the datasets](https://gist.github.com/magland/3ba2b1fe6ff138deba0edaedb5de5867#file-notebook-ipynb) -- [live notebook](https://colab.research.google.com/gist/magland/3ba2b1fe6ff138deba0edaedb5de5867) -- added 6 Nov 2018
* Step 4: Process sorting results
* Step 5: Compare with ground truth

