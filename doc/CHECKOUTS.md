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
which it maintains through ``lein hotsauce`` [subcommands](/doc/SUBCOMMANDS).

Depending on the actual direct and indirect dependencies of the current 
lein project, Hotsauce will modify the CLASSPATH according to which 
of these are hot and cold and whether Hotsauce is active 
or not.


