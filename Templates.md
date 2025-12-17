# Templates

This section provides an overview and guide to using the HSNPipeline,
including introducing the templates that are included in the pipeline.

## Table of Contents

- [Overview](#overview)
- [PrepTEMPLATE](#prep-template)
- [ConvertTEMPLATE](#convert-template)
- [AnalyzeTEMPLATE](#analyze-template)

## Overview

This guide overviews the entire pipeline, including pre-processing & spike sorting, converting
data to a standardized format, and organizing analyses. Each of these steps has it's own template.

To integrate a new task / project into the general workflow:
- Create a new pre-processing repository, following the [PrepTEMPLATE](https://github.com/HSNPipeline/PrepTEMPLATE)
    - Follow instructions in the template to pre-process and spike sort the data
- Create a new conversion repository, following the [ConvertTEMPLATE](https://github.com/HSNPipeline/ConvertTEMPLATE)
    - Follow instructions in the template for adding custom code & information, and running data conversion
- Create a new analysis repository, following the [AnalyzeTEMPLATE](https://github.com/HSNPipeline/AnalyzeTEMPLATE)
    - This repository should load NWB files, and add any custom code needed to analyze the data

Note that these steps are set up to be largely independent, so different parts of the above pipeline
can be used in isolation.

For more information & guides on these topics, see the HSNPipeline
[documentation](https://hsnpipeline.github.io/).

All of the templates in this pipeline follow the general outline of the
[StructuredScience](https://github.com/structuredscience/) layout.

## Prep Template

To get start, the pipeline provides a preprocessing template for organizing
data files and applying pre-processing procedures to get the data ready for
conversion to a standardized data format.

Notably, neuro-physiological recordings from human subjects that allow for
single-neuron detection and analyses need to be spike sorted before putative
single-neuron activity can be analyzed. The preprocessing template therefore
includes functionaltiy for spike sorting HSN data.

The [PrepTEMPLATE](https://github.com/HSNPipeline/PrepTEMPLATE)
contains a template repository for preprocessing.

## Convert Template

This pipeline uses a standard data standard and includes tools for converting data to this standard.
The goal of using a data standard is to organize data into consistent, shareable formats,
as well as to facilitate using consistent analysis protocols.

The [ConvertTEMPLATE](https://github.com/HSNPipeline/ConvertTEMPLATE)
contains a template repository for converting data into the NWB standard.

## Analyze Template

The final step for a human single-neuron project is to analyze the data.
The details of this process are necessarily quite custom for any individual project,
however where possible analyses should follow a shared basic toolkit and organization.

The [AnalyzeTEMPLATE](https://github.com/HSNPipeline/AnalyzeTEMPLATE)
repository implements a template layout for an organized analysis repository.
