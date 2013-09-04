---
layout: post
title:  "Boosting productivity"
date:   2013-09-04 23:48:37
categories: moderate tech
---

Greetings, gentlemen and ladies.

This is going to be a really quick report about things that I did
today in order to boost the speed of working with my computer.

I observed that I'm sometimes annoyingly slow doing things about which
I know that those can and should be done way quicker. And then I
started to observe myself working noticing awful thing — I'm using
touchpad. I'm using it a *lot*! Remembering how fast I was when I
didn't have this wrong muscle memory, I have started with turning it
off.

{% highlight sh %}
synclient touchpadoff=1
{% endhighlight %}

As opposed to many people who feel unfamiliar to environments that
"lack" pointing input such as mouse, trackball or touchpad, I'm pretty
comfortable with operating such an environment. It doesn't distract
you with unneeded entities and when you work with software that's
usable without mouse such as [Vim][vim], [Irssi][irssi],
[Vimperator][vimp], [TTYtter][ttytter] etc, you do things as soon as
you think of doing those. 

To justify this quite strong statement I like to say that even Korean
professional StarCraft gamers don't have perfect mouse precision
because pointing is a continuous process. Typing is more precise and
quick than pointing due to its discrete nature. And also — as some of
you may know — I prefer discrete stuff over continuous.

I proceeded to ruling out activities that require mouse, which was
quite easy. Actually, the only thing I can't do anymore on my laptop
is rapidly calling someone on Skype or answering a call. To do that I
need to turn the touchpad on (Skype, srsly, you suck). In fact, Linux
Skype client sucks so much that to fix poor navigation some cool guys
wrote [an external tool][pyimc].

Anyhow, later on I realized that my old vimrc which consisted of 139
lines of obscure snippets I was putting there since I was fifteen
doesn't fit well my new changed life because it's impossible to tweak
it, so I've decided to make a modern version of my .vimrc file,
putting things there as I need those (and surely keeping the file in
sync with my [dotfiles repository][dotf]).

I've started using Vundle today which proven to be pretty cool and
elegant way to manage .vim directory. It still has a long way to go in
order to be a definitive Vim package manager but so far it gives a
great frontend to VimScripts and a great way to stop copying your .vim
directory over all the hosts you work at.

So let me show the beginning of my new .vimrc that deals with Vundle:

{% highlight vim %}
set nocompatible
filetype off
filetype plugin indent on  " required for Vundle
let mapleader=","

" ========================================================================
" Vundle stuff
" ========================================================================
set rtp+=~/.vim/bundle/vundle/
call vundle#rc()

" ========================================================================
" Bundles
" ========================================================================
Bundle 'altercation/vim-colors-solarized'
Bundle 'wincent/Command-T'
Bundle 'Lokaltog/vim-easymotion'
{% endhighlight %}

So now after we clone Vundle in ~/.vim/bundle and issue
{% highlight vim %}
:BundleInstall
{% endhighlight %}
we'll have Solarized colors, Command-T and EasyMotion installed to our
local .vim! No need to track it in your dotfiles anymore.

I guess that an alternative to Vundler is Pathogen, but I haven't used
it and have no idea how it works and relates to this program.

So now, when we talked about the topmost part of .vimrc that deals
with leader character and vundler let's concentrate at the
minimalistic part of .vimrc that is really needed to work.

{% highlight vim %}
" ========================================================================
" Fundamentals
" ========================================================================
set t_Co=256
syntax on
set background=dark
colorscheme solarized
set smartindent
set number
set tabstop=2
set expandtab
map <C-s> <esc>:w<CR>
imap <C-s> <esc>:w<CR>a

" ========================================================================
" Less annoyance
" ========================================================================
map Q <nop>
map K <nop>
nnoremap <PageUp> <nop>
nnoremap <PageDown> <nop>
{% endhighlight %}

Yeah, that's it. Effectively it's under 20 lines of code to get stock
Vim look pretty.

We make saving using Ctrl+S possible by some obscure stty magic
(thanks, vimtips wiki!):

{% highlight sh %}
vim()
{
        local STTYOPTS="$(stty --save)"
        stty stop '' -ixoff
        command vim "$@"
        stty "$STTYOPTS"
}
{% endhighlight %}

And a little bonus for those, who survived till the end of the post —

{% highlight vim %}
" ========================================================================
" Run this file and grab the output
" ========================================================================
nnoremap <Leader>r :w<CR>o####<Esc>:r!time %:p<CR><CR>o<Esc>
nnoremap <Leader>R :w<CR>o####<Esc>:!%:p<CR><CR>o<Esc>
{% endhighlight %}

This thing runs current file in non-interactive mode but grabbing the
output and in interactive mode, printing the output as it goes. As all
the terminal emulators suck, having a VIM tab that behaves somewhat
like a terminal is great!

Hopefully, my experience and/or links in this post will be useful for
you. Type less, do more and disregard the mouse!

[vim]:     http://www.vim.org/
[vimp]:    http://www.vimperator.org/vimperator
[irssi]:   http://www.irssi.org/
[ttytter]: http://www.floodgap.com/software/ttytter/
[pyimc]:   https://github.com/crazymaik/pyimc
[dotf]:    https://github.com/manpages/dotfiles
