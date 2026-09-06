---
title: "Real-Time FPGA Image Processing Pipeline"
excerpt: "Streaming Verilog datapath for median denoising and Laplacian edge detection, sustaining one pixel per clock."
collection: portfolio
---

A fully streaming image-processing datapath on FPGA: median filtering to remove
salt-and-pepper noise, followed by Laplacian edge detection. The design
processes one pixel per clock with no external frame buffer, so pixels flow
continuously from memory to output rather than being buffered a frame at a time.

I designed the memory-interface and data-movement modules, the ROM reader and
the 3x3 sliding-window generator, and shared work on the top-level integration
and the testbench.

## Design

The sliding-window generator is the structural core of the datapath. Pixels
arrive serially, but spatial filters need to see nine neighbouring pixels at
once, spanning three different image rows. Two line buffers hold enough of the
image that a complete 3x3 window can be presented every cycle, with zero-padding
supplied at the image borders where neighbours do not exist.

Without this, a filter would have to wait for its nine input pixels to become
available one at a time, which costs at least three clock cycles per window
before any output can be produced. With the window generator supplying a
complete, aligned window on every cycle, each filter stage produces one output
per clock instead, so the pipeline reaches a steady state quickly and the
overall latency from the first input pixel to the first output pixel stays low.

The ROM reader is parameterized to handle two input formats: it either converts
24-bit RGB input to 8-bit grayscale, or routes already-grayscale input through a
matched-latency delay line, so that system timing is identical whichever format
is used.

Each module in the datapath is itself internally pipelined, breaking its
computation into several clocked stages rather than one long combinational
path. That kept the critical path short enough to raise the whole system's
operating frequency well past the original target.

## Results

The design closed timing with 2.836 ns of worst-case slack against a 75 MHz
target, giving a maximum operating frequency of 95.26 MHz. It uses 962 LUTs and
522 registers, roughly 1% of the device, plus 32% of on-chip block RAM to hold
the image itself. Static timing analysis traced the critical path to the window
generator output registers, at 8 logic levels, with 79% of the delay in routing
rather than in logic.

A three-person course project. Source on [GitHub](https://github.com/hoseinn-gh/FPGA-Image-Processing).
