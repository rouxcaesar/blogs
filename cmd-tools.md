# Leveraging the Command Line for Increased Productivity

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
I've already mentioned `tmux` in previous sections, and here I'd like to give a brief peek at how I use it. Essentially, `tmux` is a terminal multiplexer that acts as a window manager for your terminal. It allows you to create "windows" that you can cycle through, with each window serving as a complete terminal for separate tasks or processes. And in each window you can create panes that can split your screen so that you can perform separate operations in the same terminal window.

The way that `tmux` achieves this is through "sessions" which you can attach and detach from. When attached to a session, you can create a new window with a unique layout of panes that can have files open or processes running, and later detach from a session while retaining your pane layout. Many sessions, each potentially having many windows and each window with many panes.

It's best understood with some images, so here you go:

(TODO: add pic of using tmux on computer)

There are a ton of things that you can do with `tmux` and my goal here is just to introduce it as an essential tool in my workflow. If you're interested in learning more about `tmux`, check out the following links:

(TODO: add links to tmux resources)
[](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)
[](https://danielmiessler.com/study/tmux/)
[](https://sanctum.geek.nz/arabesque/zooming-tmux-panes/)
[](https://medium.com/@matthewmain/tmux-getting-started-3842b57435c0)
[](https://medium.com/@lamdbui/faster-command-line-workflow-with-tmux-a6539c8eae2c)
[](https://thoughtbot.com/upcase/tmux)

## vim
Last but not least we have vim, a text editor that comes pre-installed with every Linux and MacOS operating system. It has a reputation for being difficult to learn, but I actually found that it's not that hard so long as you have patience and learn in small chunks.

Vim allows you to edit and navigate all of your files entirely from the keyboard and those who are proficient in vim find themselves rarely using their mouse while coding. While using vim, you can navigate your cursor with the h, j, k, l keys much like old school computer games. It also has a TON of commands that you can chain together to rapidly change your code. For example, you can delete everything within a function between the `{}` characters simply by putting your cursor in the function body and typing `di{` which stands for "delete inside {}". You can perform similar functions with words, lines, paragraphs, and text inside "" or () characters, and after spending time learning vim you'll be amazed at how much more productive you can be.

The other huge plus in using vim is how customizable it is. Not only are there plenty of plugins that you can download to get specific key shortcuts, syntax coloring, and more, but you can also setup your own shortcuts by modifying your vim's configurations in a `.vimrc` file. Vim truly is a tool that you make your own and time invested in learning it is well spent.

To get started learning vim, simply go to your command line if you're on Linux or MacOS, type `vimtutor`, and hit Enter. You'll be taken to an interactive tutorial of vim that'll teach you the basics. After that, check out the following resources:

[](https://thoughtbot.com/upcase/onramp-to-vim)
[](https://thoughtbot.com/upcase/the-art-of-vim)
[](http://vimcasts.org/blog/)
[](https://pragprog.com/book/dnvim2/practical-vim-second-edition)

## Closing Thoughts

There is another plus I've found in using vim, and it's really a side effect of using it alongside `tmux` and all the other tools I've mentioned in this article. By having as much of my development workflow located in the terminal as possible, I've drastically cut down on the amount of context switching that I experience. I no longer jump between a editor where I type code to a terminal where I execute my code and tests to a browser to look at another file in the codebase on Github. I know simply start a session with tmux, create a splitscreen of two or more panes, and edit my code in vim in one pane while performing all sorts of other processes in the other panes.

In a field of work where mental energy and focus is a premium in order to perform at a high level, this benefit has helped me enormously in boosting my productivity and practicing essential command line skills. I recommend that you give it a try yourself, and start small so that you don't overload yourself. Pick up a few of the tools I've mentioned here at a time and incorporate them into your daily work. Soon enough, you'll be zipping along on the command line.
