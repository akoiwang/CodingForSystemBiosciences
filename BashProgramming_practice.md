# Linux & Bash programming - Practice

---

## INSTRUCTION 
- Run the commands by taking one command at a time and paste it in the Terminal window in GitHub Codespaces
- Try to GUESS/PREDICT what the output of the command will be 
- RUN one command at a time... did you guess correctly? 
- INVESTIGATE the command. Try to understand how it work. Ask if you get stuck. 
- YOU CAN EDIT THE CODE, and see whether the result is what you expect. 
- At some point, we will ask you to MODIFY a command to get a desired output 
- At some point, we will ask you to MAKE a line of command by yourself 
- REMEMBER: Don't be afraid of making mistakes. Don't get frightened if the screen return ERROR in red. Read the error message. It often tells you where the problems are. 
- Texts after the # sign are comments. Computer ignore these texts. You do not need to copy the comment texts to run on the Terminal.

** If confused, just ask :) ** 

---

## Checking your environment
```bash
pwd		# the output will show your current location
ls			# list content of current directory
ls Bash_exerciseFiles	# list content of `Bash_exerciseFiles` directory
ls -l			#list with more information (long list)
ls -l -h		#TODO
ls -l -h -t	#TODO
ls -lth		#TODO
```

## Navigating 
```bash
cd Bash_exerciseFiles		# change directory to `Bash_exerciseFiles` i.e. move yourself into the `Bash_exerciseFiles` directory
ls			#list the content of the directory you are in
```

## Work with files 
(Look inside, create copy rename move delete, extracting information)
```bash
ls Dataset1_15400 		# look inside the directory called `Dataset1_15400`
```

Notice that there are some files with matching suffix with folder names. Look like the keeper of these files like to keep things tidy?!

```bash
ls Dataset2				# look inside the directory called `Dataset2`
# What are the output of this command? 
#TODO

# How many files are in this directory? 
#TODO

# How big are these files?
#TODO
```

Well, it is not that tidy, is it? There are files with ID `17407` in `Dataset2` directory, and there are also some of files also beginning with `17407` outside the directory. We can use `mv` to move files (i.e. change their locations)

```bash
mv 17407_8_1.htseq-count.final Dataset2/ 	# move this file from "here" into "Dataset2"
```

We can use `*` to mean "anything and everything, including blank space and nothing"

```bash
mv 17407* Dataset2		# move any files that begin with 17407 into te directory "Dataset2"
```

Did you notice when you did `ls Dataset2` previously that there were already some files in the `Dataset2` directory? 
These files have the same names as two of the files that were moved over. What happened to the existing files with the same file names? 
#TODO

Explain how you came up with the answer above? 
#TODO

Let's do a bit more tidy-up. In our directory, all files that begin with `Smansoni` are reference from Schistosoma mansoni (a parasitic worm) genome data. Let's create a directory called `Ref_files` and move these files into the directory. 

**Note** By convention, 
- we normally capitalised the first letter of directory name. 
- For file names, we normally use all small letter. 
- Avoid using space in the file name. As you can see, space is treated with some meaning in Bash scripting )the space between command and input). Instead, use underscore (`my_file`), or mix capital letter into the middle word (`myFile`). 

```bash
mkdir reference_Smansoni		# mkdir = make directory, follow by directory name
cd reference_Smansoni		# change directory into the reference_Smansoni
#TODO						# list the content of this directory
ls ../						# list the content of the directory just one step outside our current working directory
#TODO						# move Smansoni* files from outside into this directory
#TODO						# check inside to see that all Smansoni files have been moved
#TODO						# check outside to see that all Smansoni files have been moved
```

