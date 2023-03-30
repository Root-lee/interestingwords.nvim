# vim-interestingwords

> forked from [vim-interestingwords](https://github.com/lfv89/vim-interestingwords) and rewrite with lua


vim-interestingwords highlights the occurrences of the word under the cursor throughout the buffer. Different words can be highlighted at the same time. The plugin also enables one to navigate through the highlighted words in the buffer just like one would through the results of a search.

![Screenshot](./interesting.png)
## Feature

- Highlights multiple word in same time
![Screenshot](./highlight.png)

- Navigating word under cursor, ``n`` is forward, ``N`` is backword, no matter with ``/`` or ``?`` search

- Show search count for under cursor word
![Screenshot](./search_count.png)

- Support lualine
![Screenshot](./lualine.png)

## Installation

With [packer.nvim](https://github.com/wbthomason/packer.nvim):

```
use 'Mr-LLLLL/vim-interestingwords'
```

## Usage

- Highlight with ``<Leader>k`` or search with ``<Leader>m``
- Navigate highlighted words with ``n`` and ``N``
- Clear every word highlight with ``<Leader>K`` or search with ``<Leader>M`` throughout the buffer
- Display search count with virtual text

### Highlighting Words

``<Leader>k`` will act as a **toggle**, so you can use it to highlight and remove the highlight from a given word. Note that you can highlight different words at the same time.

``<Leader>m`` will act as a **toggle**, so you can use it to search and highlight or remove search from a given word. Note that you can search a words at the same time.

### Navigating Highlights

With a highlighted word **under your cursor**, you can **navigate** through the occurrences of this word with ``n`` and ``N``, just as you would if you were using a traditional search.

### Clearing (every) Highlight

Finally, if you don't want to toggle every single highlighted word and want to clear all of them, just hit ``<Leader>K``, if you don't want to jump to search word, and cancel the search just hit ``<Leader>M``

## Configuration

The plugin comes with those default mapping, but you can change it as you like:

``` lua
    require("interesting-words").setup {
        colors = { '#aeee00', '#ff0000', '#0000ff', '#b88823', '#ffa724', '#ff2c4b' },
        search_count = true,
        navigation = true,
        search_key = "<leader>m",
        cancel_search_key = "<leader>M",
        color_key = "<leader>k",
        cancel_color_key = "<leader>K",
    }
```

support lualine config, this is not default, you need to manual added
``` lua
    require('lualine').setup{
        lualine_x = {
            ...
            {
                require("interesting-words").lualine_get,
                cond = require("interesting-words").lualine_has,
                color = { fg = "#ff9e64" },
            },
            ...
        }
    }
```
