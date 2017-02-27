---
layout: default
title:  General Projects – Summer of Code
---

# {{ page.title }}

{% include toc.html %}

## Expanding and improving LearnBase/JuliaML

[LearnBase](https://github.com/Evizero/LearnBase.jl) is an attempt to create common abstractions and tools for machine learning frameworks. Common functionality like data loading, loss functions or training processes can be defined generically, and then easily combined with a specific approach (e.g. an SVM).

Possible projects are:
  * Contributing to the generic functionality in JuliaML (e.g. creating or improving a package for loading data sets, or implementing training process, etc)
  * Pure-Julia implementations of specific model types (e.g. decision trees or SVMs) which integrate with the JuliaML ecosystem.

**Required Skills**: Knowledge of the machine learning technique(s) to be implemented.

**Recommended Skills**: General knowledge of the JuliaML project and aims, or wide knowledge of machine learning as a field, is a plus.

**Mentors**: [Christof Stocker](https://github.com/Evizero), [Tom Breloff](https://github.com/tbreloff), [JuliaML Members](https://github.com/orgs/JuliaML/people)

## Standardized dataset packaging

Scientific and technical computing often makes use of publicly available datasets. Often, there's a lot of overhead to finding these data sets and coercing them into a usable format. Packages like [RDatasets.jl](https://github.com/johnmyleswhite/RDatasets.jl/) and [MNIST.jl](https://github.com/johnmyleswhite/MNIST.jl) attempt to make this easier by downloading data automatically and providing it as a Julia data structure.

This project involves building a "[BinDeps.jl](https://github.com/JuliaLang/BinDeps.jl) for data" which would make the creation of data-providing packages easier. The package would make it easy to download / unzip large files and check their integrity them in a cross-platform way. Facilities for downloading specific datasets can then be built on top of this.

**Expected Results**: A BinDeps-like package for downloading and managing data, as well as examples of this package used with specific data sets.

**Recommended Skills**: Only standard programming skills are needed for this project. Familiarity with Julia is a plus.

**Mentors**: [JuliaML Members](https://github.com/orgs/JuliaML/people)

## Enhanced clipboard

Julia's functions for getting and setting the clipboard are currently limited to text; it would be useful to extend them to allow the transfer of other data (for example, spreadsheet data or images).

**Expected Results**: Extensible `clipboard()` and `clipboard(x)` functions to get and set the richest possible representation of the system clipboard data, as well as methods for specific types.

**Recommended skills**: Interfacing with C from Julia, clipboard APIs for different platforms. Familiarity with FileIO.jl.

**Mentors**: [Stefan Karpinski](https://github.com/StefanKarpinski)

## Calling Julia from Python

Julia could be a great replacement for C in Python projects, where it can be used to speed up bottlenecks without sacrificing ease of use. However, while the basic functionality for communicating with Julia exists in [PyCall.jl](https://github.com/JuliaPy/PyCall.jl) and [pyjulia](https://github.com/jakebolewski/pyjulia), it needs to be separated out and mantained as a real Python package.

**Expected Results**: An easy-to-use Python package which allows Julia functions to be imported and called, with transparent conversion of data.

**Recommended skills**: Familiarity with both Python and Julia, especially C interop.

**Mentors**: [Steven Johnson](https://github.com/stevengj)

## Middlewares for common web application chores in Mux.jl

Implementation of mid-level features - specifically routing, load-balancing, cookie/session handling, and authentication - in [Mux.jl](https://github.com/JuliaWeb/Mux.jl).  The implementation should be extensible enough to allow easy interfacing with different kinds of caching, databases or authentication backends. (See [Clojure/Ring](https://github.com/ring-clojure/ring/wiki/Why-Use-Ring%3F) for inspiration).

**Expected Results**: Improvements to the Mux.jl package.

**Required Skills**: Experience with web development.

**Recommended Skills**: Knowledge of various web frameworks, especially the design decisions and tradeoffs behind them.

**Mentors**: [Mike Innes](https://github.com/MikeInnes)

## QML.jl Improvements

The [QML.jl](https://github.com/barche/QML.jl) package provides Julia bindings for [Qt QML](http://doc.qt.io/qt-5/qtqml-index.html) on Windows, OS X and Linux. In the current state, basic functionality is available, but there is room for improvement regarding integration with [GLVisualize](https://github.com/JuliaGL/GLVisualize.jl) and plotting packages such as [GR](https://github.com/jheinen/GR.jl) (see also [issue 23](https://github.com/barche/QML.jl/issues/23)) or [Plots](https://github.com/JuliaPlots/Plots.jl). Another area of work is supporting more elaborate data models.

**Expected Results**: Improvements to the QML.jl package along one of these lines.

**Recommended Skills**: Familiarity with both Julia and the QT framework.

**Mentors**: [Bart Janssens](https://github.com/barche)


## Expanding the reach of Interact.jl with WebIO.jl

[Interact.jl](https://github.com/JuliaGizmos/Interact.jl), host of the popular `@manipulate` macro, is a package for interacting with Julia code using UI widgets. It currently has a couple of serious limitations:

1. It only works inside IJulia.
2. A third-party package cannot build interactive features for it (See [#38](https://github.com/JuliaGizmos/Interact.jl/issues/38) for example).

[WebIO.jl](https://github.com/shashi/WebIO.jl) is a new package for interactive HTML output in varied web-based front-ends to Julia, namely [Jupyter/IJulia](https://github.com/JuliaLang/IJulia.jl), the [Juno IDE](http://junolab.org/), [Mux](https://github.com/JuliaWeb/Mux.jl), and [Blink](https://github.com/JunoLab/Blink.jl). The idea is that these front-ends will support WebIO's display and communication API, while graphics packages like Plotls.jl or Interact.jl can build on a common counterpart display and communication API to create UIs. This means that graphics package authors need to write a widget once and it will work on all these front-ends. It also means that widgets from different packages based on WebIO.jl can be composed seamlessly.

This project involves rewriting Interact.jl using [WebIO.jl](https://github.com/shashi/WebIO.jl) to make it available on more front-ends than just IJulia.

It is a great opportunity to rethink what a package for manipulating interactive output could do. For example: can one interactively play with output from a package like Compose.jl using `@manipulate` or a similar construct (e.g. move a circle or draw a rectangle)? What would Compose.jl minimally have to do to support such interactions? How can Interact.jl help? Another scenario: can PlotlyJS use Interact.jl/WebIO.jl to support [drill down](http://www.highcharts.com/demo/column-drilldown) charts so that data can be loaded lazily from Julia as and when the user requests it? Can the state of the spreadsheet from DataFrames.jl be synced with a PlotlyJS plot?...

While these are all interesting questions to consider, the scope of this package is only to provide basic widgets (such as those in Interact.jl) and re-implement the `@manipulate` macro on top of them.

**Expected Results**: A package with basic UI widgets built on top of WebIO.jl, `@manipulate` macro with at least the same features as it does now.

**Recommended Skills**: writing generic Julia code and modular JavaScript code, writing asynchronous programs in Julia. Good aesthetic sense with UIs is a bonus!

**Mentors**: [Shashi Gowda](https://github.com/shashi)
