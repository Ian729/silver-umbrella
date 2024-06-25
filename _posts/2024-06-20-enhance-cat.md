---
toc: false
layout: post
comments: true
description: Enhance command line tool cat
categories: [markdown, tech]
title: Enhance cat
---

## Enhancement idea
The idea was to enhance command line cat
1. print files with ***syntax highlighting***
2. be able to print ***images*** to terminal

## Syntax highlighting
`bat` is a good replacement of `cat` with the following enhancement:
1. Syntax highlighting: bat supports syntax highlighting for a large number of programming and markup languages.

2. Git integration: `bat` communicates with git to show modifications with respect to the index (see left side bar).

3. Show non-printable characters such as tab/space
   
4. Automatic paging: By default, bat pipes its own output to a pager (e.g. less) if the output is too large for one screen. If you would rather bat work like cat all the time (never page output), you can set --paging=never as an option, either on the command line or in your configuration file. If you intend to alias cat to bat in your shell configuration, you can use alias cat='bat --paging=never' to preserve the default behavior.

### Installation
```
brew install bat
```


## Images
`imgcat` is a good enhancement to the `cat` command line tool.  

It's like cat but for images. (for iTerm2)

### Installation
```
brew install danielgatis/imgcat/imgcat
```

## Overwrite cat command
Next, we could overwrite the `cat` command line tool with a customized `cat` function
```
If file is an image

  use `imgcat`

else

  use `bat` to syntax highlight the file

endif
```
``` bash
cat() {
    for file in "$@"; do
        if [ -f "$file" ]; then
            # Echo the full path of the file
            full_path=$(realpath "$file")
            echo $full_path
            # Check if the file is an image
            if file --mime-type "$file" | grep -q '^.*: image/'; then
                if command -v imgcat > /dev/null 2>&1; then
                    $(which imgcat) "$file"
                else
                    echo "Error: imgcat command not found."
                    return 1
                fi
            else
                # If not an image, use bat if available, otherwise cat
                if command -v bat > /dev/null 2>&1; then
                    $(which bat) "$file"
                else
                    $(which cat) "$file"
                fi
            fi
        else
            echo "Error: $file is not a valid file."
        fi
    done
}
```

## Reference
1. https://github.com/danielgatis/imgcat
2. https://github.com/eddieantonio/imgcat
3. https://github.com/sharkdp/bat
