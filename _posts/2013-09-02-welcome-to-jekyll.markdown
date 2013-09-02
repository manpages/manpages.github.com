---
layout: post
title:  "Welcome to Jekyll!"
date:   2013-09-02 04:15:37
categories: boring tech
---

So yeah, here's [jekyll]. It's pretty awesome and pretty solarized.
I plan to add light and dark versions of the blog with light being the
default, but for now, that's how it is (not that I have written
anything interesting just yet, so if you hate dark themes, there is no
reason to read this blog just yet ;-) ).

Also I plan to add two-dimensional filter space instead of tags. This space
will have two axis — “interestingness” and “geekieness“. When I'm adding this
thing, I'll explain the idea behind (in case it isn't obvious).

Since March 1st (when I last started a Jekyll blog which was
ruthlessly destroyed along with a virtual server where it was [hosted][backup])
some changes occurred in Jekyll, pygments and highlight.js and I
really like those. 

For instance, highlight.js started to recognize Elixir programming
language!

{% highlight elixir %}
defmodule Foo.Bar.Baz do
  def foo(x) do
    [answer: 42, {"proplists", :are_not_dead}]
  end
end
{% endhighlight %}

And of course, I'd like to thank [Michishige Kaito] and [Aleksejs Popovs]
for contributing advices about blogging and css (respectively) and
being pretty awesome overall.

[jekyll]:    http://jekyllrb.com
[Michishige Kaito]: http://mkaito.github.io/
[Aleksejs Popovs]: http://popoffka.ru/
[backup]: https://en.wikipedia.org/wiki/Backup
