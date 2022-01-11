title: Normalisation In Distribution Filenames: Yet Another Packaging Vagary
authors: avi_gross
note: Post by C.A.M. Gerlach, Spyder core developer
source: https://discuss.python.org/t/revisiting-distribution-name-normalization/12348/3?u=abdur-rahmaanj
tags: packaging
slug: ---

Just sharing my own personal experience as a Python package user, developer and maintainer in both the PyPI and conda ecosystems, consistent display of a package’s display name vs. its normalized name is certainly important.

However, particularly in the large scientific Python community where both users and package authors are typically less well versed in the details of Python packaging but require large and diverse dependency stacks across different package managers to do their work, package names not following a consistent, standardized convention has posed no end of practical problems, well beyond mere aesthetics. I’ve lost count of the number of times colleagues (and myself) have wasted time and effort over trying to remember whether the import, PyPI package or Conda package name did or didn’t contain a `_`, `-` or `.`, or was UpperCamelCase or lowercase (since each can be different).

Within the Conda ecosystem, names are generally normalized to lowercase, no dot, `-` as separators (though for common cases, auto-gendered metapackages exist as aliases for `_` vs `-`), same as Linux and other package managers and I’ve found it to be much easier and more consistent to recall package names than on PyPI. And in many cases, (e.g. QtPy, a top-200 PyPI download package I maintain that sees heavy use on conda as well) the normalized name (qtpy) is actually the import name, not the project name in the metadata (QtPy) that someone long-forgotten set nearly a decade ago, when packaging conventions and knowledge were not as established as they are now.

Certainly, I don’t suggest requiring existing projects change or normalize their names, but at least as both a package user and author, normalizing user-provided names more aggressively on input, rather than less, to reduce the chance of package name confusion over aesthetic differences and the amount that users need to recall and worry about such things, is preferable to always having the display name aesthetically match whatever I (or the original author, who’s long since moved on) typed into the name field many years ago (though of course, tools still can and should display that name to users).

To add, as a package user, I’d rather work with a package with a consistent name following standard conventions that was easy to remember, than one with oddball aesthetics. As a package author, I’d much rather minimize the frustration and maximize the ease at which users install and update my package than impose particular aesthetic sensibilities, and there being an established standard to follow is much preferable to having to Google and bikeshed over how I should capitalize and punctuate the name that I will be stuck with. In fact, more normalization rather than less actually would, if anything give me more confidence rather than less if I really did want to use less conventional punctuation or capitalization, as I would be more confident that users would still find my package and not one benignly or maliciously similar.

Finally, the risk of dependency confusion, typosquatting and infrastructure attacks are not merely theoretical, it has already caused major trouble for npm, there have been attacks on PyPI and it is only likely to increase. In my view, opening the door to a whole new class of such attacks, never mind a greatly increased chance of benign developer confusion and wasted effort, is simply not worth it for a small amount of additional “creativity” (or as many would see it, the lack of a consistent convention) in package naming.


Note: Gerlach, besides being a Spyder core developer is also an atmospheric scientist, Project Mjolnir remote sensor framework creator, Ph.D student, technical writer. Currently leading a NASA-funded effort to develop a deep-learning based groundside data processing and analysis system for the GLM instrument on the GOES-R-series weather satellites.