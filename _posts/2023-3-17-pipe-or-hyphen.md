---
layout: post
title: "Success with Syncthing"
---

Piping from one cmd to another is common place in linux. 

e.g ```ls | sort```

Here, the output of the ls command is passed as input to the sort command, which sorts the file names alphabetically.

This week, I discovered the ability to use - in the terminal:

```cat - ```

This cd reads data from standard input (which can be provided by another command or entered manually) and displays it on the terminal.

```echo "This is line 1." && echo "This is line 2." | cat -```

This takes the two lines from std input and concatenates it onto a single line with output as follows:

```
This is line 1.
This is line 2.
```

Interestingly, we can use this syntax when loading data into vim:

```grep "example" file.txt | vim - ```

This takes data from stdin and loads it into vim. Fantastic!
