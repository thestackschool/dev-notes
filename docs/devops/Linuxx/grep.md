## Global Regular Expression Print

`grep` is used for searching a word in a file.

```
        grep -i 'Linux' *    (It will search for linux word in  all the files)
		grep -i 'Linux' <filename>   (it will search for linux word in given filename - ignore case)
		grep –n ‘Linux’ <filename> (to show line number where it is found)
		grep –ni ‘Linux’ <filename> (to show line number where it is found with ignore case) -/same
		grep –in ‘Linux’ <filename> (to show line number where it is found with ignore case) -/same
		grep –n -i ‘Linux’ <filename> (to show line number where it is found with ignore case) -/same
		grep -i –n ‘Linux’ <filename> (to show line number where it is found with ignore case) -/same
```

`wc(word count)`: it is used to count no.of lines, words and no.of characters of given file

```
    wc <filename>
	wc -l <filename> - gives no of lines
	wc -c <filename> - gives no of chars
```

`cp`: for copy and paste

```
    cp <oldfilename> <newfilename>
```

Note: If we want to copy more than one file data then we should go for `cat` command

    cat f1.txt f2.txt > f3.txt

`mv` : it is used for renaming & moving

    	mv  <existing-file-name>  <new-file-name>
    	mv  <source>  <destination>


## Search a file (Find and Locate)

`find` command will perform serach operation in entire linux file system. This is slower.
`locate ` will perform search operation in locate database(internal db), so this requires updating db before search. - Faster.

`locate`

	sudo yum install locate -y
	sudo updatedb
    locate <filename>


`find` - mostly used

    find <where-to search> <search-options>
	Ex:
	find <dir> -name filename (find a specific file)
	find <dir> -iname filename (ignore case in filename)
	find <dir> -type d -name dirname (find directories by name)
	find <dir> -type f -name ‘*.txt’ (find files of specific extension)
	find <dir> -type f -perm 775 (find files with specific permission type)
	find <dir> -type f ! -perm 775 (find files which are not specific permission type)
	find <dir> -type f -perm 777 -exec chmod 644 {} \; (find files with permission levels and change permission level)
	find <dir> -type f -name ‘*.txt’ -exec rm -I {} \; (find and delete files of specific extension)
	find <dir> -type f -empty (find all empty files in the directory)
	find <dir> -type d -empty (find empty sub-directories within the directory)
	find <dir> -type f -name ‘.*’ (finds all hidden files)
	find <dir> -type f -perm u=x (finds all executable files)
	find <dir> -type f -user username (finds all files to which username is owner)
	find <dir> -type f -group groupname (finds all files to which groupname is owner)
	find <dir> -mtime 5 (finds all files that were modified in last 5 days)
	find <dir> -atime 2 (finds all files that were accessed by a user in last 2 days)
	find / -type f -size +100M -exec rm -f {} \; (finds and delete all files greater than 100 mb)
	