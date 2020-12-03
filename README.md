# vim-copy-as-rtf

This plugin provides a `CopyRTF` command that copies the current buffer or
selected text to the clipboard as syntax-highlighted RTF text.

This plugin was forked from
[zerowidth/vim-copy-as-rtf](https://github.com/zerowidth/vim-copy-as-rtf),
to add support for other MS Windows and Linux/X11.


## Requirements

* The `:TOhtml` plugin, which ships with vim and is enabled by default
* One of the following environments:
    * Microsoft Windows (with PowerShell)
    * macOS (with `pbcopy` and `textutil`)
    * X11 (with `xclip`)


## Installation

Use [pathogen](https://github.com/tpope/vim-pathogen/) and clone this repo to
`~/.vim/bundle`.

## Usage

When the plugin is loaded, the following command is available:

    :CopyRTF

It operates on either the current buffer or the currently selected text. After
the command executes, the RTF text will be available on the system clipboard.

## Customization
### The `g:copy_as_rtf_preserve_indent` option
Defaults to 0.

This setting determines whether or not `:CopyRTF` will preserve the
indentation for the text it's converting. If 0, code will be outdented as much
as possible (ignoring non-code lines) before conversion.

### The `g:copy_as_rtf_using_local_buffer` option
Defaults to 0.

This setting determines whether or not temporary indentation changes (see
previous setting) are applied in the current buffer. If set to 0, the selected
code is copied to a scratch buffer before modifying it.

### The `g:copy_as_rtf_silence_on_errors` option
Defaults to 0.

This setting allows silencing the "unsupported platform" error report. By
default, if this plugin cannot find the suitable RTF support, it will report
an error. If set to a non-zero value, the plugin will silently quit under such
a circumstance.


### The `:TOhtml` plugin
The `:TOhtml` plugin can be also be configured to change how text is converted
to html before being converted to RTF. To set the font to match your MacVim or
terminal settings, use this (undocumented) setting:

    let g:html_font="Your Favorite Console Font"
