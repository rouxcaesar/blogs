# Leveraging the Command Line for Increased Productivity
	* tmux
	* vim

## Intro
As working developers grow in their career, we should always be seeking ways to improve our productivity and effectiveness. Many of us are drawn to the dazzling array of extensions, plugins, and third-party tools that claim to “boost our productivity”, but there is actually one area full of fertile ground for improvement that we all use everyday: the command line.

Nestled within the command line are a host of features and commands that can drastically improve how effectively we work, and in this article I’m going to highlight several that I’ve found helpful for me. I’ll also show you exactly how I use them on a day-to-day basis with examples. Whether you’re a beginner just starting their career or an intermediate developer with some experience, this article is for you.


## I/O Redirection
Knowing how to direct the standard input and output of your terminal is essential to boosting your productivity.  For example, let’s say that you’re working on an application and it’s giving you a ton of logs that you want to look over. Rather than having the logs simply output in your terminal so that you have to scroll through them, you can do the following:

`$ command_to_run_application &2> log-file.txt`

What this does is it runs your application and then directs all standard output including errors to a new file called `log-file.txt`. Thus all of your logs will be saved into a separate file that you can search through and share with other developers if you need help.

You can use the same method to save the output of running a large test suite into a file like so:

`$ go test -v ./ &2> test-output.txt`

In the above case, I’m running tests written in the Golang language but the I/O redirection is the same.

## pbcopy & pbpaste
Two of my favorite little features are `pbcopy` and `pbpaste` which are the copy and paste functions on the command line for MacOSX. For Linux users, there are similar commands that you can download: [How To Use Pbcopy And Pbpaste Commands On Linux - OSTechNix](https://www.ostechnix.com/how-to-use-pbcopy-and-pbpaste-commands-on-linux/)

I love these commands as they allow me to copy information from the command line without taking my hands away from the keyboard. They also make it easy to copy & paste file contents that may be difficult to accomplish with a mouse, such as with copying RSA keys to Github or other  sites like so:

`$ cat public_rsa.sh | pbcopy`

You can then simply use your keyboard shortcut for paste to dump the contents where you need to.

## grep & rgrep
With `grep` we obtain a massive superpower: the ability to find all the occurrences of a given expression in all folders and files found at a given path. This is incredibly useful for when you’re editing a file and come across a function that you need to modify or look up for more information. Using `grep` we can find every place that the function is used in milliseconds.

For example, let’s say I’m working on an API endpoint that has a `validateRequest` function and I want to see how this function is implemented. I can use `grep`  in the parent directory to easily find where the function is defined like so:

`$ grep validateRequest parent_dir/*`

(TODO: add pic of using grep on computer)

And the output will give me all the files and line numbers where we can find `validateRequest` being invoked or defined. This is extremely helpful when working with a large codebase and the execution is much faster than using the Github search feature (or what every source control solution you use).

As a bonus, I’d recommend that you look into `rgrep` which is a re-implementation of `grep` written in Rust that is several orders faster than `grep`.

(TODO: add pic of using rgrep on computer)

## less / bat
The next tool that I want to cover is `less` which allows you to interactively view the contents of a file in your terminal. This differs from `cat` or `tail` in that you can view the whole file, not just a defined set of lines at either the top or bottom of the file. 

And with `less`, you can can search through the file quickly using the `/` or `?` commands. To search in a file from your cursor down use `/` plus an expression, and to search from your cursor up use `?`. The reason you should know both is because searching in `less` does not wrap around to the beginning or end of a file, unlike with vim.

I use `less` all the time in my work because it makes it so easy to reference a file while I edit another file. If you use iTerm2 then you can edit the file in one pane while using `less` in the other. I personally use `tmux` to generate my panes and do the same.

But the real magic comes when you use `grep` and `less` together to boost your workflow! Working on a file and need to find & reference another piece of code in the codebase? Just open up another terminal tab or window (or create another pane with iTerm2 or tmux), `grep` for the code you're looking for, and then use `less` to see the inner workings!

I've found `less` to be a huge boost in my productivity and recently I've discovered `bat`, which is a re-implemenation of `less` that provides syntax highlighting, line numbering, and many other features. Give it a try!

## tmux
I've already mentioned `tmux` in previous sections, and here I'd like to give a break peek in how I use it. Essentially, `tmux` is a terminal multiplexer that acts as a window manager for your terminal. You can create panes that act as split screens so that you can perform separate operations in the same terminal window.

`tmux` also allows you to create terminal "sessions", attach to a session, create create a unique layout that could have files open or processes running, and detach from a session while retaining your pane layout.

It's best understood with some images, so here you go:

(TODO: add pic of using tmux on computer)

There are a ton of things that you can do with `tmux` and I won't be covering all of them here, so dive into the following links if you're interesting in learinging more:

(TODO: add links to tmux resources)

## pipes
Next up are pipes, which are a fundamental feature of the command line. Represented by the `|` character, pipes are used to chain commands together to achievesomething that any one command could not. Essentially, a pipe allows you to take the output of one command and use it as the input of another command.

An example of this would be 


