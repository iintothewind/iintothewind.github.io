<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/compilation-error-when-using-Comparator-comparing.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/compilation-error-when-using-Comparator-comparing.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# compilation error when using Comparator.comparing()

> Published: 2019-12-10 · Tags: java

author: Ivar.Chen
source: https://iintothewind.github.io/

## the problem
First, lets take a look at the following code sample:

```java
Collections.sort(playlist, Comparator.comparing(s -> s.getTitle())
              .thenComparing(p1 -> p1.getDuration())
              .thenComparing(p1 -> p1.getArtist())
);
```

What we are trying to do is simple: sort the `playlist` order by three different properties.
Can this code snippet pass the compilation check?
The answer is: No, there would be some compilation error.

```java
Error:(43, 59) java: cannot find symbol
  symbol:   method getTitle()
  location: variable s of type java.lang.Object
```

But why?

The reason for this compilation error is that the type inference for Java language is weak in this case.
It is expected that JVM knows what the type of the elements in `playlist` is when it is reading the first lambda `s->s.getTitle()`.
But actually, JVM is not able to figure it out.


## the solutions
There are three approaches to solve this problem.

### use static lambda expression

```java
Collections.sort(playlist, Comparator.comparing(Song::getTitle)
              .thenComparing(Song::getDuration)
              .thenComparing(Song::getArtist)
);
```

### use explicitly defined lambda with a temorary variable

```java
Comparator<Song> byName = (song1, song2) -> song1.getArtist().compareTo(song2.getArtist());
Comparator<Song> byDuration = (song1, song2) -> Integer.compare(song1.getDuration(), song2.getDuration());
Collections.sort(playlist, byName.thenComparing(byDuration));
```


### add explicity type parameter before the Comparator.comparing() is called

```java
Collections.sort(playlist, Comparator.<Song, String>comparing((s) -> s.getTitle())
              .thenComparing(p1 -> p1.getDuration())
              .thenComparing(p1 -> p1.getArtist())
);
```


## reference

[Very confused by Java 8 Comparator type inference](http://stackoverflow.com/questions/24436871/very-confused-by-java-8-comparator-type-inference)
---

> © Ivar.Chen · https://iintothewind.github.io
