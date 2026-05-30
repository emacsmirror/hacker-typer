
# Table of Contents

-   [emacs-hacker-typer](#orga803f18)
    -   [Usage](#org31ec88f)
    -   [Installation](#orgf84ce1a)
    -   [How it works](#org8caacfd)
    -   [Customization](#org6512d2d)
        -   [`hacker-typer-files`](#org3707e97)
        -   [`hacker-typer-remove-comments`](#orgc9cdaf4)
        -   [`hacker-typer-show-hackerman`](#org5951109)
        -   [`hacker-typer-type-rate`](#org4c9b45f)
        -   [`hacker-typer-random-range`](#org5a09d15)
        -   [`hacker-typer-data-dir`](#org4ab8c15)
    -   [Todo](#org60d77e9)



<a id="orga803f18"></a>

# emacs-hacker-typer

[![img](https://melpa.org/packages/hacker-typer-badge.svg)](https://melpa.org/#/hacker-typer)
[![img](https://stable.melpa.org/packages/hacker-typer-badge.svg)](https://stable.melpa.org/#/hacker-typer)
[![img](https://img.shields.io/badge/license-GPL_3-green.svg)](https://www.gnu.org/licenses/gpl-3.0.txt)

A customizable implementation of [hackertyper.com](http://hackertyper.com) in emacs.

![img](hackerman.png)


<a id="org31ec88f"></a>

## Usage

-   Type `M-x hacker-typer` and get hacking! Or use `C-u M-x hacker-typer` to be
    prompted about the file to use.

-   Type `M-x hackerman` if you'd just like a hacker companion, or `C-u M-x
       hackerman` for single-window.

-   If you'd like to see hackerman when invoking `M-x hacker-typer`, set
    `hacker-typer-show-hackerman` to `t`. See more [customization options](#org6512d2d) below.

-   You can quit with your `keyboard-quit` binding or `M-x hacker-typer-quit`.

-   You can clear downloaded data with `M-x hacker-typer-clear-cache`.

**NOTE:** None of your files are altered.


<a id="orgf84ce1a"></a>

## Installation

This package is on Melpa. To install using [use-package](https://github.com/jwiegley/use-package):

    (use-package hacker-typer
      :ensure t)

Alternatively, using [quelpa-use-package](https://github.com/quelpa/quelpa-use-package):

    (use-package hacker-typer
      :quelpa (hacker-typer
               :fetcher github
               :repo "therockmandolinist/emacs-hacker-typer"
               :files (:defaults "hackerman.png")))

Or [quelpa](https://github.com/quelpa/quelpa):

    (quelpa '(hacker-typer
              :fetcher github
              :repo "therockmandolinist/emacs-hacker-typer"
              :files (:defaults "hackerman.png")))

Otherwise, download the files to somewhere on your load path, and enable
hacker-typer:

    (require 'hacker-typer)


<a id="org8caacfd"></a>

## How it works

`M-x hacker-typer` randomly selects a file from `hacker-typer-files` (or prompts
for one if given a prefix argument) downloading it if necessary, and creates a
blank buffer with the name of that file (with random characers prepended). It
then creates a local map in which all insert, delete, and enter commands are
rebound to insert pieces of the file according to `hacker-typer-type-rate`.

`M-x hackerman` displays a humorous image of Rami Malek as "hackerman," by
inserting the file path into a temporary buffer and calling `iimage-mode`.

**NOTE:** Modes that get could get in the way are turned off if bound, so let me
know if you have more suggestions for these. The current list:

-   agressive-indent-mode
-   smartparens-mode
-   evil-smartparens-mode
-   whitespace-mode


<a id="org6512d2d"></a>

## Customization

Type `M-x customize-group hacker-typer RET` to view all customization options.

They are the following:


<a id="org3707e97"></a>

### `hacker-typer-files`

A list of files to randomly select from. Defaults to 5 emacs C source code files.

Can be web urls that point directly to files, or local files of the form:
<file:///absolute/path/to/file>.


<a id="orgc9cdaf4"></a>

### `hacker-typer-remove-comments`

If set to `t`, remove comments from files.


<a id="org5951109"></a>

### `hacker-typer-show-hackerman`

If set to `t`, shaw hackerman when calling `M-x hacker-typer`.


<a id="org4c9b45f"></a>

### `hacker-typer-type-rate`

How many characters to type out per keystroke. Can be set to:

-   `random` (default): each keystroke inserts N characters, where N is randomly
    selected from `hacker-typer-random-range`.
-   integer: types out this many characters per keystroke.


<a id="org5a09d15"></a>

### `hacker-typer-random-range`

Range from which to choose chararcters to type per keystroke if
`hacker-typer-type-rate` is set to `'random`.


<a id="org4ab8c15"></a>

### `hacker-typer-data-dir`

The directory in which to store data for hacker-typer. If [no-littering](https://github.com/tarsius/no-littering) is
installed, it defaults to `hacker-typer/` under `no-littering-var-directory`,
otherwise placing the folder under `user-emacs-directory`.


<a id="org60d77e9"></a>

## Todo

-   It's possible I should use `image-mode` to directly open the hackerman file
    instead, but I'm not sure how to do that with a temporary buffer and I like
    that temp buffers quit easily (at least, with evil-mode).

-   Somewhat relatedly, it would be nice to resize the hackerman image to fit
    the window, though this might take away from the humor of the immediacy by
    having to wait for the resize.

