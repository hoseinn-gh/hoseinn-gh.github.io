---
title: "FPGA Hardware Accelerator for JPEG AI"
excerpt: "An ongoing B.Sc. final project implementing the JPEG AI learned image compression model in hardware on FPGA."
collection: portfolio
---

An ongoing project to implement the JPEG AI image compression model in hardware on FPGA, aiming to improve its speed, resource usage or energy consumption. It is my B.Sc. final project, supervised by [Dr. Nader Karimi](https://scholar.google.com/citations?user=mZGNr2QAAAAJ&hl=en).

## Background

JPEG AI is a learned image compression standard (2025). Instead of the hand-designed transforms used by classic JPEG, it uses neural networks to turn an image into a compact latent representation, which is then entropy coded into a bitstream. The result is much better compression, but at a real computational cost.

The networks involve many layers, the intermediate feature maps of high-resolution images put heavy pressure on memory bandwidth, and the entropy coding stage takes a non-negligible share of the processing time. Together these make real-time execution difficult, especially on devices with limited resources.

## Goal

The goal is to implement the model in hardware on FPGA and improve how it runs, whether that means higher speed, lower resource usage or lower energy consumption. Dedicated hardware can fit the structure of this workload far better than a general-purpose processor, since the data flow through the layers is regular and known in advance.

## Approach

The work starts by profiling the model to see where computation, memory traffic and time actually go, and which parts limit performance. The likely candidates are the convolution layers, the movement of feature maps through memory, and the entropy coding. Those parts are then implemented in hardware and improved.

My earlier work on streaming data through on-chip buffers without an external frame buffer, in the [FPGA image processing pipeline]({{ base_path }}/portfolio/1_fpga-image-processing/), is directly relevant to the memory side of this problem.

## Status

The project is ongoing and at an early stage. This page will be updated as results become available.
