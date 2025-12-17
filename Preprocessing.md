# Pre-Processing

In this section of the guide, we outline pre-processing for human single-neuron projects.

## Overview

Collecting data for human single-neuron projects typically involves collecting
multiple data streams, for example separate collections of neural and behavioral data,
as well as potentially having other physiological recordings that need to be
integrated, such as anatomical scans.

Before this data can be integrated and analyzed, various pre-processing steps may need
to be applied. This section

Note that spike-sorting, which is considered part of pre-processing and included
in the same template, is covered on a separate Guide page.

## File Structure

A consistent file structure within and between projects, subjects, and sessions
can help to keep data files organized, and allows for programmatically finding and
processing files across the project.

To support the use of a standardized organization, HSNPipeline defines a
recommended file structure. Though it is not required to use this structure,
if you do so, HSNPipeline processes and utilities will be able to use the structure
to programmatically find and manage files.

For more information on creating and using the HSNPipeline directory structure, see
[this example](https://hsnpipeline.github.io/hsntools/auto_examples/plot_files.html)
on the `hsntools` docs.

## Resources

This pipeline uses existing external tools and to provide a template structure
for pre-processing data for HSN projects.
The key resources and tools are briefly described in this section.

Note that pre-processing may also require additional resources that are specific
to your data, for example, utilities to load or pre-process additional data formats
that are used in your investigation. In general, you should be able to integrate these
into the existing template.

As well as the below mentioned tools, pre-processing in the
HSNPipeline requires the
[hsntools](https://hsnpipeline.github.io/hsntools/) module.

### neo

To access recorded single-neuron data, we need to load and access data
which may come in various different file formats depending on the system and amplifier used.

To assist with loading various data formats, HSNPipeline uses the
[neo](https://github.com/NeuralEnsemble/python-neo) Python module, which is
a general purpose tool for loading and working with neuroscience data formats.

## Anatomical Files

In addition to neuro-electrophysiological and behavioral data, patients who are
part of human single-neuron studies will typically have some anatomical imaging
(e.g. CT and/or MRI), and these files and derived outputs from them may need to be
included in order to use anatomical information, for example the location of the
electrodes.

To do so, anatomical files can be added to the project files and analyzed as needed
to extract information of interest, which can then be added to the output files
and used during analysis.
HSNPipeline does not cover processing of anatomical files in detail, as there are
multiple other resources for managing and processing such data.
Some notes on integrating extracted information into the standardized data files
are included in the Conversion materials.

## PrepTEMPLATE

The [PrepTEMPLATE](https://github.com/HSNPipeline/PrepTEMPLATE) provides a
template structure for managing pre-processing of HSN data.
