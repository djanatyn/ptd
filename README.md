PTD - Perl To Do (List)
=======================
* * *
I've been messing with Perl for a bit, and I wanted to throw something together that was useful and fun to write. This is largely based on a previous project, htd (haskell to do) which didn't turn out so well. I learned a lot about Perl 5 in the process, and I think it might be a lot of fun to write a Perl 6 version, if I have the time.

USAGE
-----

 	ptd <action> [options]
	actions:
	-l                list all entries
	-a [entry]        add [entry] as a todo item
	-t [number]       toggle an item's todo/done status
	-r                remove all completed tasks from the list
	-r [number]       remove a specific task from the list

Nothing weird here. Each action either takes no options, or one option, with the exception of -r, which can take an option (optionally). Otherwise, it removes all completed tasks by default.

FEATURES
--------
### list entries (-l)
You can list every entry that's contained within a ".ptd" file, which currently needs to be contained within the directory you execute the script from. It organizes the tasks into done or not done, and ignores all lines that do not begin with "done:" or "todo:". You can manually edit the file yourself, if you want.

This also provides a distinct number for each item, which is used with several of the other actions.
### add entries (-a)
If you don't want to add a todo item manually, you can add it with this. Make sure that you contain your todo item within quotes, and it's probably best not to exceed 80 characters.
### toggle entries (-t)
This one was particularly fun to implement. It will toggle an item's status from 'todo' to 'done', or 'done' to 'todo'. First, you need to figure out the number that identifies the status by listing the entries. After that you can toggle that item by providing the number as the option.
### remove all completed tasks (-r)
If you want to remove all the tasks that have been completed, type this command without any options. It will remove (without confirmation!) all items that are marked as 'done'.
### remove a specific task (-r)
When you give an option to this command, it will remove that specific task, whether its completed or not. Once again, you can find each task's number by using the list command.

INSTALLATION
------------
This is still kind of a work in progress, so you're going to need a bit of technical knowledge to use it. You probably want to make the script executable and place it within your path. However, make sure that you have permissions set so that the ".ptd" file in the directory that the script is executed from is both readable and writable.

TODO
----
The script is usable as-is, but there are a couple things I might add in the future.

* add a configuration file
* organize todo files by date, and implement further options for sorting
* use Moose to refactor into object oriented code
* support for notes and other non-todo items
* expand into a PIM (Personal Information Manager)
