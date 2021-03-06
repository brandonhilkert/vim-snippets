Snipmate & UltiSnip Snippets
============================

This repository contains snippets files for various programming languages.

It is community-maintained and many people have contributed snippet files and
other improvements already.

Contents
--------

- `snippets/*`: snippets using snipmate format
- `UltiSnips/*`: snippets using UltiSnips format

Snippet engines supporting vim-snippets
----------------------------------------

There are different forks of snippet engines which allow the user to insert
snippets by typing the name of a snippet hitting the expansion mapping.

- [github.com/SirVer/ultisnips](https://github.com/SirVer/ultisnips):   
  python, supports all snippets in this repo.
- [github.com/garbas/vim-snipmate](https://github.com/garbas/vim-snipmate):   
  VimL, snipmate-snippets, engine sometimes behaves strange. Supports
  snippets/*
- [github.com/Shougo/neosnippet](https://github.com/Shougo/neosnippet.vim):   
  VimL, supports snippets/* with some configuration.
- [github.com/drmingdrmer/xptemplate](https://github.com/drmingdrmer/xptemplate):
  Totally different syntax, does not read snippets contained in this file, but
  it is also very powerful. It does not support vim-snippets (just listing it
  here for completness)
 
There tries to be a more comprehensive list (which still is incomplete) here:
http://vim-wiki.mawercer.de/wiki/topic/text-snippets-skeletons-templates.html

UltiSnips has additional features such as high speed, nesting snippets,
expanding snippets in snippets and offers powerful transformations on text in
snippets (like visual selections or placeholder texts).

Which one to use? If you have python give
[SirVer/ultisnips](https://github.com/SirVer/ultisnips) a try because its fast
and has the most features.

If you have VimL only (vim without python support) your best option is using
[garbas/vim-snipmate](https://github.com/garbas/vim-snipmate) and cope with the
minor bugs found in the engine.


Installation
------------

First be aware that there are many options, see "Snippet engines" above.
Second be aware than there are [tons of plugin managers](http://vim-wiki.mawercer.de/wiki/topic/vim%20plugin%20managment.html)
which is why Marc Weber thinks that it doesn't make sense to repeat the same
repetitive information everywhere.

*Recommended way:*
[vim-addon-manager](vim-addon-manager) (because Marc Weber wrote it for exactly
this reason, it supports simple dependency management). Eg you're done by this
line in your .vimrc:

```
" assuming you want to use snipmate snippet engine
ActivateAddons vim-snippets snipmate
```

[vim-pi](https://bitbucket.org/vimcommunity/vim-pi/issue/90/we-really-need-a-web-interface)
Is the place to discuss plugin managers and repository resources.

About how to install snipate see [snipmate@garbas](https://github.com/garbas/vim-snipmate)

(Bundle, Pathogen, git clone - keywords to make people find this link by ctrl-f search)
I know that I should be reading the docs of the snippet engine, just let me copy paste into my .vmirc:
(See this pull request)[https://github.com/honza/vim-snippets/pull/307/files].

TROUBLE
=======
If you still have trouble getting this to work create a github ticket, ask on
irc or the mailinglist.

Policies / for contributors
---------------------------

Some snippets are useful for almost all languages, so let's try to have the same
triggers for them:

```
if : if without else
ife: if $1 else $2
eif : else if ($1) { .. }
el  : else ..
wh  : while (cond) ...
```

Don't add useless placeholder default texts like
```
if (${1:condition}){
  ${2:some code here}
}
```
instead use:

```
if (${1}){
  ${2}
}
```

Exception: Functions which are used less often, such as Vim's matchall(), matchstr()
functions which case hints may be helpful to remember order. In the VimL case
get vim-dev plugin which has function completion

Thus for conditions (while, if ..) and block bodies just use ${N} - Thanks

Open questions:
What about one line if ee then .. else .. vs if \n .. then \n ... \n else \n .. ?
Which additional policies to add?
Discuss at: https://github.com/honza/vim-snippets/issues/230


Related repositories
--------------------
We also encourage people to maintain sets of snippets for particular use cases
so that all users can benefit from them.  People can list their snippet repositories here:

     * https://github.com/rbonvall/snipmate-snippets-bib (snippets for BibTeX files)
     * https://github.com/sudar/vim-arduino-snippets (snippets for Arduino files)
     * https://github.com/zedr/zope-snipmate-bundle.git (snippets for Python, TAL and ZCML)
     * https://github.com/bonsaiben/bootstrap-snippets (snippets for Twitter Bootstrap markup, in HTML and Haml)

Installation using VAM: "github:rbonvall/snipmate-snippets-bib"

Future - ideas - examples
-------------------------

[overview snippet engines](http://vim-wiki.mawercer.de/wiki/topic/text-snippets-skeletons-templates.html)
If you have ideas you can add them to that list of "snippet engine features by example".


Historical notes
----------------

[vim-snipmate][1] was originally started by [Michael Sanders][2] who has now
unfortunately abandoned the project. [Rok Garbas][3] is now maintaining a
[fork][4] of the project in hopes of improving the existing code base.

Versions / dialects / ..
========================
There are some issues, such as newer language versions may require other
snippets than older. If this exists we currently recommend doing this:

add snippets/ruby.snippets (common snippets)
add snippets/ruby-1.8.snippets (1.8 only)
add snippets/ruby-1.9.snippets (1.9 only)

then configure github.com/garbas/vim-snipmate this way:


```vim
let g:snipMate = {}
let g:snipMate.scope_aliases = {}
let g:snipMate.scope_aliases['ruby'] = 'ruby,ruby-rails,ruby-1.9'
```

If it happens that you work on a project requiring ruby-1.8 snippets instead,
consider using vim-addon-local-vimrc and override the filetypes.

Well - of course it may not make sense to create a new file for each
ruby-library-version triplet. Sometimes postfixing a name such as

    migrate_lib_20_down
    migrate_lib_20_up

will do it then if syntax has changed.


Language maintainers
--------------------

No one can really be proficient in all programming languages. If you would like
to maintain snippets for a language, please get in touch.

Notes: People are interested in snippets - and their interest may wane again.
This list is kept up-to-date on a best effort basis.

* Python - [honza](http://github.com/honza)
* Javascript - [honza](http://github.com/honza)
* HTML Django - [honza](http://github.com/honza)
* Markdown - [honza](http://github.com/honza)
* Ruby - [taq](http://github.com/taq)
* PHP - [chrisyue](http://github.com/chrisyue)
* Scala - [gorodinskiy](https://github.com/gorodinskiy)
* Falcon - [steveno](https://github.com/steveno)
* Elixir - [iurifq](https://github.com/iurifq)

Contributing notes
------------------

Until further work is done on `vim-snipmate`, please don't add folding markers
into snippets. `vim-snipmate` has some comments about how to patch all snippets
on the fly adding those.

Because UltiSnips reads snipmate-snippets too there is no need to duplicate all
snippets - only those snippets who use advanced UltiSnips features should be
duplicated in UltiSnips.

Currently all snippets from UltiSnips have been put into UltiSnips - some work
on merging should be done (dropping duplicates etc)

License
-------

Just as the original snipMate plugin, all the snippets are licensed under the
terms of the MIT license.


[1]: http://github.com/garbas/vim-snipmate
[2]: http://github.com/msanders
[3]: http://github.com/garbas
[4]: http://github.com/garbas/vim-snipmate
[7]: http://github.com/SirVer/ultisnips
