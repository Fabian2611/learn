---
title: A beginner's intro to Strudel
---

[Strudel](https://strudel.cc/workshop/getting-started/) is a great tool to get started in making music, without having to work through complex DAW layouts, music theory and midi editors.
It comes with tons of instrument samples and synthesizers, right there in your browser. But its documentation is pretty bad at showing how easy it really is to get started,
even without ever having made music before.

# Using Strudel
Before we code in Strudel, you should probably know how to even play your song. Press *play*!
<iframe 
  src="https://strudel.cc/#c291bmQoImNhc2lvIik%3D"
  width="100%"
  style="border: none; border-radius: 12px; overflow: hidden;"
  scrolling="no"
  loading="lazy">
</iframe>

...and it's working! Told you it was easy.

This is, by the way, just an embedded version of the [strudel.cc](https://strudel.cc/#c291bmQoImNhc2lvIik%3D) website. You can use that just as easily!

# Sounds
Strudel has a bunch of different sounds; `casio` is just one of them. Try replacing `casio` in the above box with `insect`, `wind`, `jazz`, `metal` or `crow`.
Then just press *play* again, or, if the previous sound is still playing, press *update*.

# Sequences of sounds (or, beats)
Just one sound is boring. Let's play some more!
<iframe 
  src="https://strudel.cc/#c291bmQoImJkIGhoIHNkIG9oIik%3D"
  width="100%"
  style="border: none; border-radius: 12px; overflow: hidden;"
  scrolling="no"
  loading="lazy">
</iframe>

These random characters stand for different parts of a drum set. The most important ones are:
> **bd** - bass drum </br>
> **sd** - snare drum </br>
> **rim** - rimshot (striking the snare drum and its metal rim simultaneously) </br>
> **hh** - hihat </br>
> **oh** - open hihat </br>
> **lt** - low tom </br>
> **mt** - mid tom </br>
> **ht** - high tom </br>
> **rd** - ride cymbal </br>
> **cr** - crash cymbal </br>

Try them out!

# Actual beats
Try adding more sounds to the code above, without deleting any old ones.

You may notice, that the more notes you add inside of the quotation marks, the faster they are played. This seems weird; you'd expect them to just be played one after another.

This is where Strudel differs from the usual music making software. Instead of thinking in beats (one sound after the other), it thinks in cycles. A cycle has a fixed length, by default 2 seconds, and every
`sound` statement fills exactly one cycle with the sounds you give it. This means, in the previous example of four sounds (`bd hh sd oh`) in the `sound` function, each one takes `2s / 4 = 0.5s`.

The solution for this is the `<...>` syntax. Every element inside angled brackets will play for exactly one cycle - instead of the whole sequence being squished into one cycle. Let's hear it!

<iframe 
  src="https://strudel.cc/#c291bmQoIjxiZCBoaCBzZCBvaD4iKQ%3D%3D"
  width="100%"
  style="border: none; border-radius: 12px; overflow: hidden;"
  scrolling="no"
  loading="lazy">
</iframe>

Try adding more notes inside the angled brackets, and notice how the tempo (speed) doesn't change.
To stop us from falling asleep, we need more than one sound per cycle though. That's awfully slow.

>[!Remember]
> Strudel uses cycles instead of beats to regulate its tempo.</br>
> By default, a function like `sound` tries to squish all its elements into a single cycle.</br>
> Angled brackets make every element inside it take exactly one cycle, avoiding said squishing.

# Making it faster (or slower)

Strudel has very convenient syntax for speeding things up: just append `*X`, where X is the factor you want to speed it up by. For example:

<iframe 
  src="https://strudel.cc/#c291bmQoIjxiZCBoaCBzZCBvaD4qMiIp"
  width="100%"
  style="border: none; border-radius: 12px; overflow: hidden;" 
  scrolling="no"
  loading="lazy">
</iframe>

Try changing the 2 to different integers, or even decimal numbers (like `2.5`)!
If you were to change the factor to `0.5`, it would be only half speed. There's also a different syntax for that exact same thing: `/2`.

>[!Remember]
> `*` means speed up </br>
> `/` means slow down


# Grouping notes

Especially when coming from making music in DAWs or composing, thinking in cycles may be slightly counterintuitive to you.
But there's a solution for that: an element inside angled brackets can not just be a sound, it can also be a block of sounds. You can group notes together in blocks using square bracket notation (`[...]`).

Try placing some square brackets around `bd hh` in the previous example, making it `[bd hh]`. Each sound now only takes half the time it used to, because it's sharing the single cycle it gets with another sound.

Mixing these notations allows us to create proper beats, that can look similar to drum sequencing software:

<iframe 
  src="https://strudel.cc/#c291bmQoYDwKW2JkIGhoIHNkIGhoXSBbYmQgaGggLSAgaGhdClstICAtICBoaCBoaF0gW29oIC0gIC0gIGhoXQo%2BYCk%3D"
  width="100%"
  height="200"
  style="border: none; border-radius: 12px; overflow: hidden;" 
  scrolling="no"
  loading="lazy">
</iframe>

> [!Tip]
> Instead of writing hundreds of characters in a single line, I like splitting my code into multiple lines. For this, just replace the quotation marks (`" "`) with backticks (<code>\` \`</code>). </br></br>
> I also snuck another piece of new syntax into this: `-` (or `~`) just stands for a rest, or pause; so playing no sound at all.

While listening, try to predict where the white cursor is currently, even if it's invisible. That should help you get a feel for the rhythm.

> In music theory terms: each square bracket block is a measure, every sound inside it a beat. A measure is just a block of sounds played in a fixed amount of time, just like our `[...]` block when enclosed in angled brackets.

Notice how, like earlier, the sounds within each block split the time equally between them. Try extending the example by even more blocks of four!

You can also try experimenting with 3, 6 or even 8 sounds in a single block. Each block still only takes exactly one cycle of two seconds, while the beat appears to be getting faster, because the time is split between more notes.

# Advanced syntax

The way `*` was used earlier is actually a bit of a special case, because it usually works differently. You can actually also use it to play a sound multiple times in the time a single sound would usually take.
For example:

<iframe 
  src="https://strudel.cc/#c291bmQoImJkIGhoKjIgcmltIGhoKjMgYmQgWy0gaGgqMl0gcmltIGhoKjIiKQouX3BpYW5vcm9sbCgp"
  width="100%"
  height="200"
  style="border: none; border-radius: 12px; overflow: hidden;"
  scrolling="no"
  loading="lazy">
</iframe>

> [!Tip]
> Appending `._pianoroll()` to a pattern gives you this neat little visualisation below it.

Here, `hh*2` would be equivalent to `[hh hh]` (two hihats in the time of one block). `[- hh*2]` expands to `[- [hh hh]]`.

Let's analyze the latter notation:
The block splits its time between two elements: a rest (`-`), and another block. That inner block splits its time again between two hihats. This means, that the rest will take half the block's time, while
each hihat individually only takes a quarter of the block's time.

This math-sy approach to rhythm is useful if you're comfortable with maths - if not, that's not an issue at all. You feel rhythm, and for that you don't have to understand the maths behind it.

# Playing many sounds at once
Before ending this article, I want to quickly teach you one more piece of syntax you'll definitely need along the way: labels.
Labels allow you to play more than one line simultaneously. They look like this:

<iframe 
  src="https://strudel.cc/#JDogc291bmQoImJkIC0gc2QgLSIpCiQ6IHNvdW5kKCJoaCBoaCBoaCBoaCIp"
  width="100%"
  height="200"
  style="border: none; border-radius: 12px; overflow: hidden;"
  scrolling="no"
  loading="lazy">
</iframe>

Just add `$:` before each of your lines. This will make them play in parallel.

# ...and that's it!
That's all for this little introductory article. You may have noticed how this is still pretty close to the official Strudel docs - but changing the order of a few things, and explaining some parts more thoroughly.
I also left out lots of stuff that I think is not that important for beginners, in order to keep this article compact.

I'll stray way farther from the official docs soon, so that hopefully, by the end, you will have made your first own song in Strudel!

The next article will be about playing notes, and writing your first own melody. If you have any wishes for future tutorials, or any feedback, please do comment below!
