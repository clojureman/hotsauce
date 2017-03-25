# Hotsauce *vs.* checkouts

*Optional reading*

### Changes to projects
Checkouts are symlinks to other projects that have to be placed 
inside the project itself. When these links are place, the source 
of the projects they point to is used instead of the source being 
fetched from a repo.

Hotsauce *as a matter of principle* does not change anything in the projects or the project files.

Instead it keeps the list of hot projects in ``~/.hotsauce``, which it
maintains through ``lein hotsauce`` subcommands.

