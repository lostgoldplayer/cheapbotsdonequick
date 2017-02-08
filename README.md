# Making twitter bots using Cheap Bots, Done Quick!

[Cheap Bots, Done Quick!](http://cheapbotsdonequick.com/) is a platform for generative Twitter bots.

It uses [Tracery](https://github.com/galaxykate/tracery) to generate content from JSON source.

At it's simplest, it turns this:
```javascript
{
  "origin" : "Hello World"
}
```
into this:
```
Hello World
```

Tokens (wrapped with a hash like `#this#`) are expanded from this:
```javascript
{
  "origin" : "Hello #planets#",
  "planets" : ["Mercury", "Venus", "Mars", "Earth"]
}
```
into any of these (it picks a value randomly each time it runs):
```
Hello Mercury
Hello Venus
Hello Mars
Hello Earth
```

Here's one of the best Cheap Bots Done Quick tutorials - http://barrl.net/2767

Text tweets are great, but the reason that I love Cheap Bots Done Quick is that you can create and tweet images using SVG.

<a href="https://twitter.com/sadkeanubot"><img src="https://pbs.twimg.com/media/C4CyQpaXAAAAssZ.jpg:large" width="20%" /></a>
<a href="https://twitter.com/superclipartbot"><img src="https://pbs.twimg.com/media/C4JHhlqWYAA2s6N.png:large" width="20%" /></a>
<a href="https://twitter.com/badphotoquality"><img src="https://pbs.twimg.com/media/C4FfBLVWQAA0DxE.jpg:large" width="20%" /></a>
<a href="https://twitter.com/time4gametheory"><img src="https://pbs.twimg.com/media/C4FuJerW8AA4jOn.jpg:large" width="20%" /></a>

## Tutorials
* [Make your own New Yorker cartoon Twitter bot](https://github.com/derekahmedzai/cheapbotsdonequick/blob/master/new-yorker.md)
