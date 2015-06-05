# Different Vim commands, a cheat sheet

`:h {command}` - help page on the *command*  
[Vim's Wiki](http://vim.wikia.com)

### Files  

###### Open a file from the current buffer  
`e: path/fname` - open fname  
`e: <Space><C-d>` - list all available directories/files  
`e:` `<Tab><Tab>...` - cycle through all availabe items  

###### Moving between files
`:bn` and `:bp` - move to the next\previous buffer in the list  
`:ls` - list all available buffers  
`:b#` - move between two last used (primary) buffers
`:bf` and `:bl` - first and last
`:bm` - next modified

###### Saving/quitting  
`:w`, `:wq` - write/write-and-close  
`:x` - write buffer if there was a modification  
`:qa!` - quit everything, ignore changes everywhere  
`:wqa` - the opposite  

###### Creating new files  
`:new [fname]` - create empty buffer with horizontal split window  
`:enew [fname]` - within the current buffer  
`:vnew [fname]` - vertical split window  
`:tabnew [fname]` - buffer within new tab  
`:only` - closes all the split windows until there is only one window left open  
`autocmd BufNewFile *.template` # added to .vimrc - new file from template  

###### Switching the working directory  
`:cd ~/new/path` - go to ~/new/path  
`:pwd` - display path to current directory  
`:lcd ~/new/path` - change directory only for current window
