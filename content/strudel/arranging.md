---
title: Arranging a song
---

A small one off article on combining many sections into a full song.

# Using `cat`
`cat` concatenates several notes or blocks to each other, making each take one cycle. This is the same as wrapping your pattern in `<...>`. For example:
<iframe 
  src="https://strudel.cc/#Y2F0KCJlNSIsICJiNCIsIFsiZDUiLCAiYzUiXSkubm90ZSgpCi8vICI8ZTUgYjQgW2Q1IGM1XT4iLm5vdGUoKQ%3D%3D"
  width="100%"
  style="border: none; border-radius: 12px; overflow: hidden;" 
  scrolling="no"
  loading="lazy">
</iframe>

The active and the commented line are equivalent. This is most useful when using variables:

<iframe 
  src="https://strudel.cc/#Y29uc3QgcGFydEEgPSAiZTUiCmNvbnN0IHBhcnRCID0gImI0Igpjb25zdCBwYXJ0QyA9ICJbZDUgYzVdIgpjYXQocGFydEEsIHBhcnRCLCBwYXJ0Qykubm90ZSgp"
  width="100%"
  height="200"
  style="border: none; border-radius: 12px; overflow: hidden;" 
  scrolling="no"
  loading="lazy">
</iframe>

To make each element inside `cat` take e.g. two cycles, append `.slow(2)` to the function. You can also use it as a chained function instead, writing:

```js
partA.cat(partB)
```

instead of:

```js
cat(partA, partB)
```

# Using `arrange`
`arrange` is probably the best option to create long songs with several section, such as a verse and chorus. Arrange takes any amount of arguments, where each
argument specifies for how long it should play, and what notes to play. For example (on a very simplified version of Blue Rondo a la Turk):

<iframe 
  src="https://strudel.cc/#JHBpYW5vOiBhcnJhbmdlKAogIFs4LCBub3RlKGA8CiAgW0EgRiBBIEYgQSBGIEUgRiBHXSBbQSBGIEEgRiBBIEYgQmIgQSBHXSBbQSBGIEEgRiBBIEYgRSBGIEddIFtGIEcgQSBHIEEgQmIgQSBCYiBDNF0KICBbQSBGIEEgRiBBIEYgRSBGIEddIFtBIEYgQSBGIEEgRiBCYiBBIEddIFtBIEYgQSBGIEEgRiBFIEYgR10gW0YgRyBBIEcgQSBCYiBBIEJiIEM0XQogID5gKV0sCgogIFs4LCBub3RlKGA8CiAgW0cgXyBHYiBfIEYgXyBFIF8gX10gW0QjIF8gRSBfIEYgXyBGIyBfIF9dIFtHIF8gR2IgXyBGIF8gRWIgXyBfXSBbRSBfIF8gRiBfIF8gRiMgXyBfXQogIFtHIF8gR2IgXyBGIF8gRWIgXyBfXSBbRSBfIEYgXyBGIyBfIEcgXyBfXSBbRiMgXyBGIF8gRSBfIEViIF8gX10gW0UgXyBfIEYgXyBfIEYjIF8gX10KICA%2BYCldCikuYWRkKG5vdGUoMTIpKS5zb3VuZCgicGlhbm8iKS5nYWluKCI8MC43ITggMC40ITg%2BIikucmVsZWFzZSgwLjQp"
  width="100%"
  height="400"
  style="border: none; border-radius: 12px; overflow: hidden;" 
  scrolling="no"
  loading="lazy">
</iframe>

There are two parameters to arrange, each taking `8` cycles. An alternative way of doing this:

<iframe 
  src="https://strudel.cc/#bGV0IHBpYW5vQSA9IG5vdGUoYDwKICBbQSBGIEEgRiBBIEYgRSBGIEddIFtBIEYgQSBGIEEgRiBCYiBBIEddIFtBIEYgQSBGIEEgRiBFIEYgR10gW0YgRyBBIEcgQSBCYiBBIEJiIEM0XQogIFtBIEYgQSBGIEEgRiBFIEYgR10gW0EgRiBBIEYgQSBGIEJiIEEgR10gW0EgRiBBIEYgQSBGIEUgRiBHXSBbRiBHIEEgRyBBIEJiIEEgQmIgQzRdCiAgPmApCgpsZXQgcGlhbm9CID0gbm90ZShgPAogIFtHIF8gR2IgXyBGIF8gRSBfIF9dIFtEIyBfIEUgXyBGIF8gRiMgXyBfXSBbRyBfIEdiIF8gRiBfIEViIF8gX10gW0UgXyBfIEYgXyBfIEYjIF8gX10KICBbRyBfIEdiIF8gRiBfIEViIF8gX10gW0UgXyBGIF8gRiMgXyBHIF8gX10gW0YjIF8gRiBfIEUgXyBFYiBfIF9dIFtFIF8gXyBGIF8gXyBGIyBfIF9dCiAgPmApCgphcnJhbmdlKAogIFs4LCBwaWFub0FdLAogIFs4LCBwaWFub0JdCikuYWRkKG5vdGUoMTIpKS5zb3VuZCgicGlhbm8iKS5nYWluKCI8MC43ITggMC40ITg%2BIikucmVsZWFzZSgwLjQpCg%3D%3D"
  width="100%"
  height="500"
  style="border: none; border-radius: 12px; overflow: hidden;" 
  scrolling="no"
  loading="lazy">
</iframe>

You can also add more instruments by using `stack`:

```js
arrange(
  [8, stack(pianoA, bassA, clarinetA)],
  [8, stack(pianoB, bassB, clarinetB)]
)
```

For this, you should append the `.sound(...)` and other FX to the variable declarations, instead of below the arrange.

This can also be used to add a few measures of silence (e.g. `[8, note("-")]` for 8 silent measures) before a new instrument enters.

> [!Info]
> `stack(...)` plays all elements inside it in parallel. It has the same behaviour you would get from prepending `$:` to several lines.

# Using `mask`
Whenever the current number inside of `.mask(...)` is `0`,  the instrument is silent. Whenever it's `1`, it plays. By automating its parameter, you can turn instruments on and off during your song:

<iframe 
  src="https://strudel.cc/#bGV0IHBpYW5vID0gbm90ZShgPAogIFtBIEYgQSBGIEEgRiBFIEYgR10gW0EgRiBBIEYgQSBGIEJiIEEgR10gW0EgRiBBIEYgQSBGIEUgRiBHXSBbRiBHIEEgRyBBIEJiIEEgQmIgQzRdCiAgPmApCgpsZXQgY2hvcmRzID0gbm90ZShgPAogIFtbRixFNF0gW0YsRWI0XSBbRixENF0gW0YsQyM0XUAxLjVdIFtbRixDNF0gW0YsQyM0XSBbRixENF0gW0YsRWI0XUAxLjVdCiAgW1tGLEU0XSBbRixFYjRdIFtGLEQ0XSBbRixDIzRdQDEuNV0gW1tGLEM0XSAtQDAuNSBbRixDIzRdIC1AMC41IFtGLEQ0XSAtQDAuNV0KICAgIAogIFtbRixFNF0gW0YsRWI0XSBbRixENF0gW0YsQyM0XUAxLjVdIFtbRixDNF0gW0YsQyM0XSBbRixENF0gW0YsRWI0XUAxLjVdCiAgW1tGLEU0XSBbRixFYjRdIFtGLEQ0XSBbRixDIzRdQDEuNV0gW1tGLEM0XSAtQDAuNSBbRixDIzRdIC1AMC41IFtGLEQ0XSAtQDAuNV0KICA%2BYCkKCiQ6IHBpYW5vLmFkZChub3RlKDEyKSkuc291bmQoInBpYW5vIikuZ2FpbigiPDAuNyE4IDAuNCE4PiIpLnJlbGVhc2UoMC40KS5tYXNrKCI8MCAwIDAgMCAxIDEgMSAxPiIpCgokOiBjaG9yZHMuc291bmQoInBpYW5vIikuZ2FpbigwLjUpLnN1c3RhaW4oMC41KS5yZWxlYXNlKDAuMikK"
  width="100%"
  height="500"
  style="border: none; border-radius: 12px; overflow: hidden;" 
  scrolling="no"
  loading="lazy">
</iframe>

Mask is thus `0` for 4 cycles, and `1` for 4 cycles. The melody is silent for 4 measures, then plays for 4. You can also simplify `.mask("<0 0 0 0 1 1 1 1>")` to `.mask("<0@4 1@4>")`.

This and `arrange` can solve the same problems; although `arrange` is usually more compact.
