# Hotsauce
*- say goodbye to checkouts*

> * Hot load source code and resources from libraries *(including transitive dependencies).*
> * No changes to your projects or project.clj
> * No monkey business with symlinks

## It's time to spice up your library development

For anything but toy projects, it essential to break up the code into separate libraries.

In the Clojure world this works great, but there's a little problem.

### The problem
It is a hassle to work simultaneously on a Clojure project and the libraries
it depends on.
<br>
Whenever a change is made to a source file of a library, that library has to be built, 
installed in a repo, and the main project has to be rebuilt. Only then can 
you run your code and check if the change worked or not.

Worse yet, you might have libraries in you application that depend on the library you 
changed, so you need to rebuild those as well before rebuilding the application.

*This goes counter to the try-it-out-now culture so central to the cult of the REPL.*

It is no wonder that some people opt to 
[cowboy code](https://en.wikipedia.org/wiki/Cowboy_coding), 
refraining from properly partitioning their code into separately versioned libraries.

### Checkouts
Leiningen acknowledges the problem and offers a partial solution called checkouts.
It works well, but [it can be bothersome and error-prone](/doc/CHECKOUTS.md).

### The solution

Add some Hotsauce! 

Hotsauce is built on the same idea as checkouts, but removes most of the hassle.

### How it works

Let's say you have some projects that depend on libraries x and y, and that 
the source code of these has been checked out to your local filesystem.

 * Register the local path with Hotsauce:
   
   ``lein hotsauce path-to-lib-x path-to-lib-y``
   
 * Make the libraries **hot** by typing
   
   ``lein hotsauce hot x y``
   
 * Make sure Hotsauce is active by typing
 
   ``lein hotsauce on``
   
   (You can always turn Hotsauce off again with ``lein hotsauce off``)
   
Leiningen will now do all its normal tasks on any project as, *fetching 
source and resources related to project x and y from the local filesystem*.

Suddenly the local source is hot!

Start the main projects with your favourite IDE or just ``lein repl``, 
and you can edit and reload source files from x and y to your 
heart's content. You don't even have to worry if the version 
numbers correspond to what the main projects declare.

When you are done and sure that it all works (yes, ``lein test`` 
also respects hot projects), just turn Hotsauce off 
again, and bump version numbers, check in etc. as you would do normally.

## Install

I recommend making Hotsauce available for all of your projects.

If you have no `~/.lein/profiles.clj` file, you could just create one 
and give it this content:

```clojure
{:user {:plugins [[hotsauce "0.1.5"]] }}
```

> If you already have a ~/.lein/profiles.clj file, you will
  <br>need to add `[hotsauce "0.1.5"]` to the `:plugins` vector.

## Good news if you work in a team
Using Hotsauce can be an individual decision that impacts nobody else. 

> But if you want to make life extra easy for team members, you might 
  want to include the Hotsauce plugin in the project.clj of your main projects, 
  so it will be automatically available for everybody.
  <br>Just add `[hotsauce "0.1.5"]` to the `:plugins` vector inside ``defproject`` in ``project.clj``

## Want to know more?
Actually, what you have read so far on this page should be 
enough to get you going.
  
However, here's a bit more:
  
  * [List of subcommands](/doc/SUBCOMMANDS.md)
  * [Tutorial - yet to be written](/doc/TUTORIAL.md)

## ClojureScript must wait
Hotsauce is spicey, but still in beta.
I'm pondering how to best support figwheel/cljsbuild, so for now you'd better stick to using it for Clojure

## Contributors
* *You name could go here*
* *or maybe here...*

Pull requests are welcome.

## License

Copyright © 2017 Mads Olsen

Distributed under the Eclipse Public License version 1.0
