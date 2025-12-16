# HSN Pipeline

HSNPipeline is a pipeline for processing and analyzing single-neuron data from human subjects.

## Table of Contents

- [Overview](#overview)
- [Guides](#guides)
- [Templates](#templates)
- [Resources](#resources)
- [Tools](#tools)
- [Contributing](#contributing)

## Overview

HSNPipeline includes templates, code, and resources for
working with human single-neuron (HSN) data.

This pipeline implements and uses standardized tools and data formats,
organized into a standard workflow that can be used for human single-neuron data.
In doing so, it pulls from and adopts existing resources from across neuroscience,
curated and extended such that they support the specifics of human single-neuron data.

On this website, you will find guides for key steps of working with the HSNPipeline data,
including pre-processing & spike sorting, conversion to a standardized data format,
and data analysis.

## Templates

This pipeline is organized into multiple components, including:
- PREP: basic pre-processing of HSN related data, including spike sorting
    - This is available in the [PrepTEMPLATE](https://github.com/HSNPipeline/PrepTEMPLATE)
- CONVERT: converting the data to a standardized data format (NWB)
    - This is available in the [ConvertTEMPLATE](https://github.com/HSNPipeline/ConvertTEMPLATE)
- ANALYZE: analyzing HSN data, including task-based analyses
    - This is available in the [AnalyzeTEMPLATE](https://github.com/HSNPipeline/AnalyzeTEMPLATE)

## Resources

Other resources that may be useful include:
- This [tutorial](https://github.com/HSNPipeline/SpikeTutorial) introduces working with spike data

### Spike Resources

As part of the
[OpenLists](https://openlists.github.io/) project,
there is a maintained list of
[spike resources](https://github.com/openlists/SpikeResources).

This list details tools and resources related to working with single-neuron data.

### Spike Interface

For running spike-sorting, we recommend the
[spikeinterface](https://github.com/SpikeInterface/spikeinterface)
tool for managing and running spike sorting.

SpikeInterface is a tool for creating flexible and robust
spike-sorting pipelines, including supporting access to a large
number of existing spike sorters.

### Neurodata Without Borders

The data standard used in this pipeline is the
[NWB](https://www.nwb.org/) file format.
NWB is a general-purpose data standard for neurophysiological data.

See the
[NWBexamples](https://github.com/HSNPipeline/NWBExamples)
repository for some examples NWB files.

## Tools

This pipeline also has associated software tools that are available to be used with the pipeline.

Note that these tools are organized as independent Python modules and thus can
be used with or without using the broader pipeline.

### hsntools

The [hsntools](https://github.com/HSNPipeline/hsntools)
mini-module contains general utilities for working with the HSN pipeline.

This module is required for using the templates provided by the pipeline.

### spiketools

The [spiketools](https://github.com/spiketools/spiketools)
module is an open-source collection of analysis tools for working with
single-neuron data, specifically designed for analyzing human data.

Spiketools implements general analysis code, which can be used for
analyzing data across tasks and contexts.

## Contributing

'HSNPipeline' welcomes contributions and suggestions from the community!

If you would suggest an edit to a part of the project, please open an issue on Github,
on the relevant repository, and/or directly open a pull request with the suggested update.

Note that to interact with the HSNPipeline organization you must follow the
[Code of Conduct](https://github.com/HSNPipeline/Overview/blob/main/CODE_OF_CONDUCT.md).
