# Hotsauce *vs.* checkouts

*Optional reading*

### Changes to projects
Checkouts are symlinks to other projects that have to be placed 
inside the project itself. When these links are place, the source 
of the projects they point to is used instead of the source being 
fetched from a repo.

Hotsauce *as a matter of principle* does not change anything in 
the projects or the project files.

Instead it keeps a list of hot (or cold) projects in ``~/.hotsauce``, 
which it maintains through ``lein hotsauce`` [subcommands](/doc/SUBCOMMANDS.md).

Depending on the actual direct and indirect dependencies of the current 
lein project, Hotsauce will adapt the CLASSPATH (and ``:cljsbuild :builds`` in case of ClojureScript) 
according to which of these are hot and cold and whether Hotsauce is active 
or not.

### Versions
One of the ways Hotsauce differs from checkouts is that it can be used 
without access to a matching repository version of the hot dependencies.  
Actually hot dependencies do not even have to be installed in a repo.

### Clojurescript
Hotsauce emulates the CLASSPATH ordering (by shadowing `:clsjbuild :builds ... :source-path`), whereas `cljsbuild` makes its own attempt 
at interpreting checkouts in a way meant to be compatible with standard lein.
I suspect that Hotsauce gives a result that is actually more like standard lein - but to be honest, I'm not sure.