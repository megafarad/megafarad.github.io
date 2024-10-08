---
layout: post
title: Introducing Ve-scala
subtitle: A port of a simplified wrapper of a Japanese language morphological analyzer.
gh-repo: megafarad/Ve-scala
gh-badge: [star, fork, follow]
comments: true
author: Chris Carrington
---

# What is it?
A Scala port of <a href="https://github.com/Kimtaro/ve">Ve</a> by Kim Ahlström. A linguistic framework for anyone. No degree required.

* **Segments Japanese morphemes into "words"** via <a href="https://github.com/atilika/kuromoji">Kuromoji</a>.
* Based on the <a href="https://github.com/Kimtaro/ve/tree/master/java">Java port</a> of <b><a href="https://github.com/shirakaba/">Jamie Birch</a></b>, original <a href="https://github.com/Kimtaro/ve">Ruby implementation</a> by <b><a href="https://github.com/Kimtaro/">Kim Ahlström</a></b>

# Usage

First, add the following dependency:

```
libraryDependencies += "com.megafarad" % "ve-scala-core" % "0.2.1"
```

Then, pick a parser and use it.

For Japanese:
```scala
import com.megafarad.ve_scala.japanese.KuromojiIpadic

val sentence = "お寿司が食べたい。"
val parser = new KuromojiIpadic(sentence)

parser.words.foreach {
  word => println(word.word + " -> " + word.partOfSpeech)
}
/*
お -> Prefix
寿司 -> Noun
が -> Postposition
食べたい -> Verb
。 -> Symbol 
 */
```

For English:

```scala
import com.megafarad.ve_scala.english.StanfordNLPEn

val sentence = "I want to eat sushi."
val parser = new StanfordNLPEn(sentence)

parser.words.foreach {
  word => println(word.word + " -> " + word.partOfSpeech)
}

/*
I -> Pronoun
want -> Verb
to -> Preposition
eat -> Verb
sushi -> Noun
. -> Punctuation
 */
```



