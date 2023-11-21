---
title: How to install DisCoPy
tags: Research
status: Seedling
---
Here are some tips for a smooth installation experience for installing the DisCoPy Python package so that you can use it in Jupyter notebooks through Anaconda.

Links:

- GitHub README page: [https://github.com/discopy](https://github.com/discopy)
- GitHub repository: [https://github.com/discopy/discopy](https://github.com/discopy/discopy)

On the pages above it says to just run `pip install discopy` for a quick installation. However, when I did this I got a few error messages when running the following code (from [this documentation page](https://docs.discopy.org/en/main/notebooks/qnlp.html#DisCoCat)):

```python
from discopy.grammar.pregroup import Ty, Id, Word, Cup, Diagram

n, s = Ty('n'), Ty('s')

Alice = Word("Alice", n)
loves = Word("loves", n.r @ s @ n.l)
Bob = Word("Bob", n)

grammar = Cup(n, n.r) @ s @ Cup(n.l, n)

sentence = Alice @ loves @ Bob >> grammar
sentence.draw(figsize=(5, 5))
```
The error message I got was: `TypeError: Expected discopy.monoidal.Diagram, got Ty('s') of type discopy.rigid.Ty instead.`

When I ran the `pip freeze | grep discopy` command to check which version of DisCoPy the pip install had installed, I discovered that it had installed version 0.6.0 and not the latest version (1.1.4 on the day of writing this).

I then tried to download and install the released version 1.1.4 through [https://github.com/discopy/discopy/releases/tag/1.1.4](https://github.com/discopy/discopy/releases/tag/1.1.4), but I didn't manage to get it to work.

In the end, I found [this](https://github.com/discopy/discopy/issues/11) GitHub issue and decided to install DisCoPy as suggested in the issue:

```bash
git clone https://github.com/oxford-quantum-group/discopy.git
cd discopy
pip install .
```
However, to be able to use DisCoPy in Jupyter notebooks through Anaconda, I had to do the following:

- Create a new Conda environment: `conda create --name discopy_env`
- Activate the environment: `conda activate discopy_env`
- Install a Python kernel in the Conda environment: `conda install ipykernel`

https://github.com/hidaris/thingtalk/issues/9

https://stackoverflow.com/questions/58568175/upgrade-to-python-3-8-using-conda

https://stackoverflow.com/questions/42231764/how-can-i-rename-a-conda-environment








