# Leveraging the Command Line for Increased Productivity
	* grep / rgrep
	* less / bat
	* I/O redirection to create log files
	* pipes to chain programs
	* pbcopy, pbpaste, Linux versions
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



## grep & rgrep

## less / bat

## pipes





