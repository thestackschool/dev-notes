# Working with Directories in Linux

`$mkdir` : it is used to create/make directory.

`$rmdir` : it is used to remove only empty directory.

`$rm -r  <dirname>` : It is used to delete non-empty directories.

`$cd <dirname>`  : Change directory

`$cd ..`  : Come out from the directory

`$ls -l <dirname>` : list the content of given directory

`$cat <filename>`   : It will display all the data available in the file

`$head`  : It will display first 10 lines of the file  from top  (`10` is the default count)

			head  <filename>  (it will give first 10 lines of data)
			head  -n  15 <filename>     (it will give first 15 lines of data)
			head  -n  25 <filename>   (it will give first 25 lines of data)

`$tail`   :  It will display last 10 lines of the file from bottom (10 is the default count)

                tail  <filename>   (it will give last 10 lines data)
                tail -n 15 <filename>   (it will give last 15 lines data)
                tail -n 25 <filename> (it will give last 25 lines data)

                tail -n 50 <filename> (it will give last 50 lines data)
                tail -n +50 <filename> (it will give data from 50th line to till last line)
            
** Note: To get latest data from file we need to use 'tail' command because lastest data will be appended at bottom
