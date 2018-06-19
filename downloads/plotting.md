---
layout: default
title:  Plotting in Julia
---

# Plotting in Julia

Plotting in Julia is available through external packages.

## Plots

[Plots.jl](https://github.com/JuliaPlots/Plots.jl) is a plotting metapackage which
brings many different plotting packages under a single API, making it easy to swap
between plotting "backends". Installation and example usage is as follows:

{% highlight julia %}
Pkg.add("Plots")
using Plots
plotly() # Choose the Plotly.jl backend for web interactivity
plot(rand(5,5),linewidth=2,title="My Plot")
Pkg.add("PyPlot") # Install a different backend
pyplot() # Switch to using the PyPlot.jl backend
plot(rand(5,5),linewidth=2,title="My Plot") # The same plotting command works
{% endhighlight %}

A guide to the available backends can be found [in the manual](http://docs.juliaplots.org/latest/backends/).
Additionally, many Julia packages add plotting functionality through its [recipe system](http://docs.juliaplots.org/latest/recipes/).
These can be used to do tasks like creating a default visualization
for Julia types and create entirely new types of plots.
[The ecosystems page](http://docs.juliaplots.org/latest/ecosystem/) shows some
visualizations the extension packages have added to Plots.jl.

## PyPlot

[PyPlot](https://github.com/JuliaPy/PyPlot.jl) uses the Julia PyCall
package to call Python's matplotlib directly from Julia with little or
no overhead (arrays are passed without making a copy). Make sure that
Python and MatPlotlib are correctly installed. Installation of
PyPlot.jl and example usage are as follows:

{% highlight julia %}
Pkg.add("PyPlot")
using PyPlot
x = linspace(0,2*pi,1000); y = sin.(3*x + 4*cos.(2*x))
plot(x, y, color="red", linewidth=2.0, linestyle="--")
{% endhighlight %}

## Gadfly

Gadfly is an implementation of a
[Wickham-Wilkinson](http://www.cs.uic.edu/%7Ewilkinson/TheGrammarOfGraphics/GOG.html)
style grammar of graphics in Julia. Add the Gadfly package to your
Julia installation with the following command on the Julia prompt:

{% highlight julia %}
Pkg.add("Gadfly")
using Gadfly
draw(SVG("output.svg", 6inch, 3inch), plot([sin, cos], 0, 25))
{% endhighlight %}

Gadfly's interface will be familiar to users of R's
[ggplot2](http://ggplot2.org) package. See
examples and documentation on the [Gadfly](http://gadflyjl.org) homepage.
