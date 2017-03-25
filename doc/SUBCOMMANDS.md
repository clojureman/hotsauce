# Subcommands 

You can get a list of subcommands by typing

``lein help hotsauce``

subcommand|what it does
-----------|------------
add | Adds one or more projects to hotsource control.<br>*- You can specify project directories or project files.*
add-recursive |  Add all projects under current directory to hotsauce
remove        |  Remove a project from the project list
hot           |  Hot-sauce one or more projects.
cold          |  Exempt one ore more projects from hot-saucing
on            |  Makes hotsauce active
off           |  Makes hotsauce active
show          |  Show the effective project settings as lein sees them.<br>*- Use mostly if you are interested in lein internals*
-----------|------------

If you just type 

``lein hotsauce``
 
you will get a list of all projects added (and not removed).
These will either have status hot or cold, and this be shown on list.

#### Explanation of output 
If ``-->`` is shown, if means that the project is a direct or indirect dependency of the current project.

If Hotsauce is active, ``*`` will be shown next to a project, 
if that project is both *hot* and a direct or indirect 
dependency for the current project.