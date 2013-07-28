# BACON - Deliciously Maintainable CSS

## Current Thoughts

I've spent the past couple of days thinking about what I like and what I dislike about these strategies, and what I'd like to see in a strategy. The following is what I'm looking to cover in this new strategy:

* Variable, Mixin, and Extendable Classes
* Style Guides
	* Element Guides
	* Component Guides
* CSS Naming Conventions
* Separation of architecture vs implementation

I've got some of the more high-level pieces figured out already I think. For me, the separation of architecture and implementation, and the creating of a reusable Style Guide have been fairly well encompassed in [Style Prototypes](https://github.com/Team-Sass/generator-style-prototype). I also think that we can leverage preprocessing for mixins and extendables for properties that get shared across multiple pieces. [Toolkit's Contributing Guide](https://github.com/Team-Sass/toolkit/blob/1.x.x/CONTRIBUTING.md) does a fairly good job at breaking down how that would work, with good examples being [Intrinsic Ratios](https://github.com/Team-Sass/toolkit/blob/1.x.x/compass/stylesheets/toolkit/_intrinsic-ratio.scss) and [Clearfix](https://github.com/Team-Sass/toolkit/blob/1.x.x/compass/stylesheets/toolkit/_clearfix.scss). These mixins are designed to be either extended or write properties directly and are written in such a way as to make implementation easy. Mixins and extendables like this would be part of the Style Guide.

Naming conventions and strategy are the big thing that I'm still working through. I will fully admit, I haven't implemented what I'm about to propose yet, but rather is based on my experiences. I prefer semantic naming of classes, describing their purpose, to functional naming (maybe highlighted instead of border-red). This way, the same semantics can be used to produce varied results. Either way, it's all subject to change, but this is what I've got:

### Bases

These are the variables, mixins, and extendables that power your Style/Component guides. They are core patterns that are shared by multiple components/objects/nuances.

### Components

These are classes, without prefix, to be used as styling anchor points (and, of course, can include styling in and of themselves). Components will probably be equally used inside of Style/Component guides and in individual implementations. They are similar to blocks in BEM and modules in SMACSS and  OOCSS.

<pre><code class="language-scss">.component{}
</code></pre>


### Objects

These are classes, prefixed with an underscore, to be used to style individual pieces that could be used to make up a component. Objects will mostly be used in Style/Component guides, with individual changes happening inside of implementations, probably using a Component as an anchor for a change. They are similar to elements in BEM and sub-modules in SMACSS.

<pre><code class="language-scss">_object{}
</code></pre>


### Nuances

These are classes, prefixed with a dash, to be used to alter the appearance of a component or object. They are similar to modifiers in BEM, themes in SMACSS, and skins in OOCSS.

<pre><code class="language-scss">.-nuance{}
</code></pre>


### Grids and Layout

When building grids and layouts, I prefer to use semantic grid frameworks like [Singularity](https://github.com/Team-Sass/Singularity/wiki) as well as asymmetric grids. These do not lend themselves well to grid classes, nor would I really want them to. I find grid classes make maintaining your layouts hard. I haven't quite figured out exactly where I would prefer to put them, but my initial feeling is that they are implementation specific and would be defined inside of an implementation. They would pivot off of components or objects, but not entirely sure yet.