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
- Notice the syntax of each command. They may seem to differ slightly from one another but there is some common patterns. 

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

## Look into files
```bash
cd ../						# change directory to one step outside the current working directory
pwd							# check where you are
cat mart_export_1.txt			# display all content of mart_export_1.txt file on the terminal console - you might not want to do this for most files. It will make Terminal look messy, and it's not very informative
head mart_export_1.txt		# show the first 10 lines of the file
tail mart_export_1.txt			# #TODO
less mart_export_1.txt		# open the file in a controllable window. Try using up-arrow and down-arrow to scroll up and down the page. Try typing gg and Shift+g. Can you tell what happened? #TODO
```

You might notice that the mart_export_1.txt is actually in FASTA format. Let's rename the file to have `.fasta` ending instead of `.txt`

Previuosly we see `mv` can __move__ files to a new location. 
`mv` can also be used to __rename__ a file.

```bash
mv mart_export_1.txt mart_export_1.fastq		# rename the file. The syntax of command is mv currentfilename newfilename
```

Now let's explore `mart_export 2.txt` next

```bash
#TODO						# use a Bash command to with the first 10 lines of mart_export 2.txt. Notice the space in the file name. Use internet to find out how to deal with file name with space. 
#TODO						# rename the mart_export 2.txt into something is more representative of its content. It is always a good idea to give meaningful names to your files
```

We can create a new text file, copy, and remove. 
```bash
touch myNewFile.txt			# create a new empty file
code myNewFile.txt			# open the file in the coding console in GitHub Codespace
cp myNewFile.txt myNewFile2.txt	# make a copy into a new file name
#TODO						# how would you copy the file myNewFile.txt into a different directory? Say into a new directory called TestFile? 
```

## Directing output 

The `mart_export_1.fasta` seems to have a couple of sequences. Let's say we are only interested in the sequence name, so that we have some idea of what kind of data this `fasta` file is holding. Notice the pattern in any `fasta` file, the header line will start with `>` sign. 

```bash
grep '>' mart_export_1.fasta		# grep/take any lines in mart_export_1.fasta that match the > pattern
```

We could count the number of sequence by eyes, but in real life we won't!! There might be 1,000 or 1,000,000!!

```bash
grep '>' mart_export_1.fasta | wc	# the output of grep command here is the fasta header line by line. The output of grep is passed to wc via the pipe | symbol and used as input for wc. wc do word count (and also line count) 

# We could also keep the output of grep to a new file first, and then use wc on that file

grep '>' mart_export_1.fasta > fastaHeader.txt	# the > symbol after a command mean "directing the output (that would otherwise display on a screen) of this command into the file as named on the right"
wc fastaHeader.txt
```

We can use `>` or `>>` for directing screen output to a file. What are the differences between using `>` or `>>`? 
Use the space below to experiment and investigate how these two symbol work

```bash
#TODO - add the commands you ran to investigate the differences between > and >> 
#TODO - explain the differences between using > and >> 
```
```bash
# Hint: one is append, one is overwrite. 
```

Say we now don't really need the `fastaHeader.txt` file anymore. We can remove it using `rm`

```bash
rm fastaHeader.txt		# remove the file
ls						check that it's gone
```

Did you get any _"warning"_ or _"are you sure you want to delete?!"_ prompt before the file was removed? The warning is not a default for Linux. It will just delete! And the files will not be in the Recycle Bin either. They will just be GONE! after the `rm` command. 

We can make the warning prompt the default at least for our log-in profile. 
We change this in the `.bashrc` profile. `.bashrc` contain multiple built-in commands that will run every time a new Terminal window is open. 

```bash
cd				# go to our home directory
code .bashrc
```

This will open .bashrc file in the coding space. Look for the part where it says `alias`

**See if you can guess what it's doing from it's syntax?** #TODO

Try adding another alias command that says "when I say `rm` what I mean is `rm -i` 
Explain how you editted the `alias` part here #TODO

Test whether your edit work:
```bash
source .bashrc
#TODO			# create a new empty just to test
rm				# did you get a warning prompt to confirm your delete? 

---

WELL DONE!!!! We have covered much of the basic Bash Programming that will alllow you to be more familiar with the coding system for the follow weeks. You will also be using Bash a lot when analysing high-throughput data. There are more commands in Bash and Linux that we have not covered here but once you are familiar with Bash scripting, exploring those commands on-the-job will be more fulfilling than cramping them in now! 

However, for those extra keen minds, feel free to explore and test yourself with more challenges below. They will show you more ways that Linux and Bash scripting can help you handle bioinformatic files with grace. Your assignment for week 2 ends HERE!! The rest of the content below is for fun. 

Try learning the following functions using the `mart_export 2.txt` as input, or using a `gff` file.
Manipulating column data : `sort`, `uniq`, `cut`, `paste`
String editor : `sed`	
Pattern search and more : `awk`	

Challenge 1: How many lines are there in total for the `mini_GFF.gff` file?
(Hint: `wc -l filename`)

Challenge 2: How many lines are there in total for each `.fa` or `fasta` file?
(Hint: `wc -l fastafile`) (Hint 2: use *)

Challenge 3: Try the same commands on `real_FASTA.fa` and `real_GFF.gff`
- In `real_GFF.gff` files, check how many lines contain information about “CDS”
(Hint: use `grep “patterntomatch” filename` combine with `wc -l` using pipe ( `|` ))
	In mini_FASTA and real_FASTA, check how many sequences the file contain. (Hint, each sequence will contain a header line, starting with >)

On real_GFF file, 
	select only “CDS” information from chromosome “Schisto_mansoni.Chr_2.unplaced.SC_0213” 
(Hint: use grep twice connect by pipe ( | ))
	and save this information to a new file
(Hint: use > or >> )

Using file from the previous command
	extract gene ID, 
	keep only unique ID, 
	then sort by ID 
	and save this information to a new file




BONUS:

- In Bash, you can adjust colour display and how your username appear on the command prompt. 
- Go to your home directory (doing just `cd` with no destination address with take you to your `home`)
- Do `ls -a`. This will list all files in the directory, including hidden files (start with .)
- There should be a file called `.bashrc` in your home directory.
- Open in file in the coding space in GitHub Codespace.
- Some part of this file define how your Bash username is displayed and coloured. It also say how folders and files should be coloured. (by default, it will be plain black&white!). 
- Find out where in the .bashrc file determine this formatting feature, and try editting it. 
**MAKE SURE YOU MAKE A COPY OF THE ORIGINAL COPY OF `.bashrc` FILE BEFORE EDITING IT**
- The file `.bachrc` normally run automatically every time a new Terminal window is opened. You can also force run it while in session by doing `source ./.bashrc`
