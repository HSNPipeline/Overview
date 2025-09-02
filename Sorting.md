# Sorting

In this first section of the guide, we outline information related to
pre-processing neural recordings, including spike sorting.

## Overview

After neural data has been collected, the first key pre-processing step is spike sorting.

Note that HSUPipeline does not implement or offer any spike sorters -
all spike sorting should be done with an existing / external spike sorter.

To support spike sorting, HSUPipeline offers a template structure for
doing spike sorting with it's preferred spike sorter (combinato).
Note that using this pipeline overall does not depend on using this particular
spike sorter (or the sorting template). If collected data is already sorted
and/or is to be sorted with a different spike sorter, you can skip ahead.

## Resources

This template uses a series of existing tools and resources to provide a procedure for managing
spike sorting. The key resources and tools are briefly described in this section.

### Combinato

The current template uses [Combinato](https://github.com/jniediek/combinato/)
for spike sorting.

Combinato is a Python tool for spike sorting:
- For tutorials and documentation, see the
[Wiki](https://github.com/jniediek/combinato/wiki/)
- Combinato is described in
[this paper](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0166598)

### neo

To run spike sorting, we need to load and access neural data - which may come in various
different file formats depending on the system and amplifier used.

As a general purpose tool to load variable different neuroscience data formats,
this template uses the [neo](https://github.com/NeuralEnsemble/python-neo)
Python module.

### Other Spike Sorters & Resources

Note that there are many other available spike sorters -
for resources and a list of available spike sorters, see the
[Spike Resources](https://github.com/openlists/SpikeResources#spike-sorting) open list.

Additional Resources:
- [Past, present and future of spike sorting techniques](https://www.sciencedirect.com/science/article/pii/S0361923015000684)
- [Quality Metrics to Accompany Spike Sorting of Extracellular Signals](https://www.jneurosci.org/content/31/24/8699.short)

### Spike Interface

In future iterations, the template is likely to be updated to use
[SpikeInterface](https://github.com/SpikeInterface/spikeinterface)

SpikeInterface is a Python based workflow tool for spike sorting:
- For more information, see the
[documentation](https://spikeinterface.readthedocs.io/en/latest/)
- SpikeInterface is described in
[this paper](https://elifesciences.org/articles/61834)

## SortTEMPLATE

The [SortTEMPLATE](https://github.com/HSUPipeline/SortTEMPLATE) provides a
template structure for managing spike sorting.

Briefly, this template includes:
- An organized layout and utilities for running the `combinato` spike sorter, including helper code and functions to run automatic spike detection procedures, and guidance on doing manual curation.
- An export process for extracting curated spike sorting results ready to be loaded and stored in the output files during the data conversion process.

## Running Combinato

Notes on using the Combinato spike sorter:

### Automatic Processing Notes

- Event detecting requires a detection polarity (positive or negative)
    - Only one polarity can be run at a time
    - BlackRock & Ripple: typically always negative polarity
    - Neuralynx: uses positive polarity
- By default, Combinato defaults to 2 rounds of template matching, but this can be changed to do more

### Manual Curation

GUI Actions:
- To select a cluster press 'enter'
  - This highlights the selected cluster across the visualizations
- To mark a cluster as bad click 'A' for artifact
  - This moves a cluster to the 'Artifacts' group
- To move a cluster, in "AllGroups" click (select) a cluster, and then click the new location to move it to
- To merge a cluster to an existing other cluster:
    - from "All Groups", click on cluster to move and then click an existing cluster to move it to
- To separate out a cluster to a new (empty) cluster:
    - click on Actions / New Group to create a new (empty) cluster
    - From "All Groups", click on the cluster to split out, then to the new (empty) group to move it there

GUI Notes:
- The GUI has 3 categories of clusters: artifacts, unassigned, assigned clusters
- The cluster colors:
    - dark blue: events from the first template matching
    - light blue: events from the second template matching
    - orange: spikes matched to the cluster
- The GUI has buttons for labeling a cluster as 'SU' (single-unit), 'MU' (multi-unit), or 'Artifact'
    - DO NOT use these labels to mark artifacts, as this does not move or remove the cluster, just gives it a label

Curation Notes:
- It is generally normal that some channels but no detected spikes, but if whole electrode bundles or subjects have no detected events, you should check the original data, and see if something can be done to improve spike yields (by doing something to the data, and/or tweaking combinato settings).
- While it is worth quickly checking automatically designated "artifact" & "unassigned" clusters, combinato is usually good at automatically designating this, and this rarely has to be changed.
- In general, the usual situation is Combinato will detect more clusters / groups than appear to be real units, meaning it is very common to reject clusters / groups and/or merge clusters. As such, the typical outcome of manual curation is to end up with fewer groups than automatically detected.
- Real units (that can be analyzed) are ideally present across the whole recording. If a unit is only detected during a specific / short time periodic it is likely an artifact. If it does appear to be a real unit (e.g. has a nice waveform), check for other clusters that might reflect the same unit at different time ranges, in case the unit was split and needs to be recombined.
- For ISIs, ideally real units should have less than \~3% of spikes within 3 ms.

### Combinato Output Files

Combinato saves out and edits a custom set of files.
To move to the next part of the pipeline (converting data to NWB), we need to load
and extract

This process can be done with the `extract_sorted.py` Python script that is included in the Sorting
Template. For more information about what files this process loads, and how they are organized, see the
[sorting IO](https://github.com/HSUPipeline/hsntools/blob/main/hsntools/sorting/io.py) functionality in hsntools.

Combinato uses the following language within it's files:
- `class`: events collected together through the clustering process
- `group`: clusters joined together by the cluster matching process

## Run Procedures

The following is the basic process for
- Organize neural data into the expected data structure for the pipeline
- Use the provided python and shell scripts to run automated event detection
- Do manual curation (see guidance below) to fine tune spike sorting results
- Extract the curated spike sorting results

```
# Split channel data files to be ready for spike detection
python scripts/split_files.py

# Run the automated spike sorting (in folder of channel files)
sh run_sorting.sh

# Do manual curation (with the Combinato GUI - see notes below)

# Extract sorted and curated spike sorting results
python scripts/convert_data.py
```