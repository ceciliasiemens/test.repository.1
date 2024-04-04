# HPC Computing Pratical Protocol

Participant: **Cecilia Siemens**

Immatriculation number: **12459567**

Course moodle page: [Moodle](https://moodle.lmu.de/course/view.php?id=25931#section-4)

# Table of Contents
1. [Introduction](#introduction)  
    1.1. [About HPCs](#aboutHPCs)
    1.2. [My Motivation](#mymotivation)  
    1.3. [My Expectations](#myexpectations)  
2. [Git/GitHub](#github)  
    2.1. [Version Control](#versioncontrol)  
    2.2. [Markdown](#markdown)  
3. [Linux](#linux)  
    3.1. [Introduction to Linux](#introductiontolinux)  
    3.2. [Navigation](#navigation)  
    3.3. [Basic Commands](#basiccommands)  
4. [Working with Data](#workingwithdata)  
    4.1. [Connect to HPCs](#connecttoHPCs)  
    4.2. [Work on an HPC](#workonanHPC)  
    4.3. [Scripting](#scripting)  
    4.4. [Syntax of Scripting](#syntaxofscripting)  
    4.5. [Task: BacGenome](#taskbacgenome)  
5. [SLURM](#slurm)  
    5.1. [Introduction to SLURM](#introductiontoslurm)  
    5.2. [Basic SLURM Commands](#basicslurmcommands)  
    5.3. [Task: SLURM](#taskslurm)  
6. [Alignment Programs](#alignmentprograms)  
    6.1. [Introduction to Alignment Programs](#introductiontoalignmentprograms)  
    6.2. [Task: Aliscale](#taskaliscale)  
7. [Containerization and Dockers](#containerizationanddockers)   
    7.1. [Introduction to Containerization and Dockers](#introductiontocontainerizationanddockers)  
    7.2. [Task: Diamond](#taskdiamond)  
8. [Project BacGenStat](#projectbacgenstat)  
9. [Personal Conclusion](#personalconclusion) 
---

# 1. Introduction <a name="introduction"></a> 
### 1.1. About HPCs <a name="aboutHPCs"></a>
High-Performance Computing (HPC), as the name suggests, refers to the use of powerful computing systems that are capable of processing and analyzing large volumes of data at high speeds. HPC systems are organized into clusters, which are groups of computers that contain anywhere from 10 to 1000 servers, also known as “nodes”. Each node in an HPC system is equipped with several processors, or Central Processing Units (CPUs), each containing between 8 to 80 cores depending on the specific HPC system configuration. This is in huge contrast to Personal Computers (PCs), which typically only have one or two CPUs with up to 16 cores. In addition to their superior processing power, HPC nodes also have substantial memory storage, ranging from many terabytes to up to 500 exabytes. Each node also has networking capabilities, allowing different nodes to connect through an InfiniBand that supports up to 100 Gb/s.  
Unlike typical PCs, HPC systems do not have human interface options such as monitors, keyboards, or mices. Usually one requires a standard PC (or a laptop server) to connect to and work with an HPC. We log in remotely by using specialized terminal software or SSH clients and connect to the login nodes, which are separate from the actual compute nodes. After logging in, we gain access to storage and two different types of compute nodes: one for simpler tasks and another for specialized tasks that require more power or larger memory.

### 1.2. My Motivation <a name="mymotivation"></a>
In today’s world, skills such as programming are becoming increasingly important, and it’s beneficial to at least understand the basics. This is especially true in the field of High Performance Computing (HPC), which plays a great role in advancing biological research.  
As a biologist with an interest in microbiology, I will be dealing with vast amounts of data generated from experiments, sequencing, or imaging. Programming skills could help me to process and analyze these datasets quickly.

### 1.3. My Expectations <a name="myexpectations"></a>
I am looking forward to learning the basic knowledge and skills in scripting and programming, as well as gaining an understanding of how HPCs function and how to use them effectively. In particular, I hope to enhance my ability to solve problems independently, which includes learning how to identify mistakes in my scripts and find specific commands online. Furthermore, I am excited to get to work with different types of data and to explore a range of tools that might be beneficial in my studies and future career.

# 2. Git/GitHub <a name="github"></a>
### 2.1. Version Control <a name="versioncontrol"></a>
Version control is a system used to track, manage, and document changes to files and projects over time, enabling multiple people to work on a project simultaneously.  
There are various version control systems, including distributed systems like Git. The Git structure is as follows: firstly, you have the working directory, where you work on files yourself. This directory contains all the files and folders of your project. Changes from the working directory can then be staged using the `git add` command, transferring them to the staging area, an intermediate step between the working directory and the local repository. The staging area is used to select specific changes and prepare them for the next commit. After staging changes, the `git commit` command transfers them to the local repository. Each commit is typically accompanied by a message describing the changes made, serving as documentation for other developers to understand why certain changes were made. The local repository stores the complete version history of your project on your computer. After committing changes to the local repository, you can upload them to the remote repository using the `git push` command. The remote repository, often hosted on a server like GitHub, makes your changes available to other developers for sharing or collaboration. If other developers have made changes to a project and uploaded them to the remote repository, you can download these changes to your local repository with the `git pull` command, staying up to date and integrating others' changes into your working directory.  
A branch is a copy of the code in a repository that can be edited independently of other branches, enabling parallel development lines. Branches can be created, deleted, merged, and compared.

### 2.2. Markdown <a name="markdown"></a>

#### 2.2.1. Introduction
Markdown is a lightweight markup language that is used to format plain text documents. It allows users to add formatting elements such as headers, lists, links, or emphasis (such as bold or italic text) using simple syntax. By using straightforward symbols and characters, such as asterisks (*) or dashes (-), Markdown indicates formatting elements, making it easy for users to remember and use.

#### 2.2.2. Headers
Headers in Markdown are created by adding "#" in front of the text. The number of hash symbols determines the header level. More hash symbols indicate a lower level header.
### This Headline uses three Hashtags  
##### This Headline uses five Hashtags
To underline a header, you can add three or more dashes "-" or asterisks "*" underneath the header text. However, headers with one or two hashtag symbols typically already have an underline.
##### This Headline uses five Hashtags and has an Underline
---

#### 2.2.3. Emphasis
To create *italic* text, enclose the desired text within single asterisks (*) or underscores (_). For **bold** text, use double asterisks (**) or underscores (__). To strike through text, employ double tildes (~~) before and after the text.

#### 2.2.4. Lists
Lists can start with a random numer followed by a fullstop or can start with other symbols such as "*", "+", or "-". To create unordered sub-list you can use two spaces and a symbol. 
1. first ordered list item
- List item with a dash
  - Unordered sub-list (using two spaces and a dash).  
  If you add two spaces behind a line,  
  it leads to a line break without a new paragraph.
3. Lists can start with any number

#### 2.2.5. Links
Links can typically be created using square brackets [] for the link text and parentheses () to enclose the URL: [example link](https://www.google.com)

#### 2.2.6. Images
You can also include images in your text as an useful tool. There are different ways of doing so. The original Markdown version involves using an exclamation mark (!) followed by square brackets [] containing the alt text of your image, followed by parentheses () containing the URL of the image.  

![funny meme](https://uploads-ssl.webflow.com/5f3c19f18169b62a0d0bf387/60d33be8cf4ba7565123c8bc_YPD3ulQQAGQpOcnqIm3QzSTRgzmr1SexpW9ZjMpJ1mAnUxx4iF05XOTu44sk0qQG-8XgBcYmGZGAD-5SAZvJl3TjtmhgWnn-w0C2XKwhBscV78RVvhwZfyp0v_Pa6sNj5zxpOvRW.png)
_Figure 1: Funny meme as demonstration of how to insert an image into your document using code._  

However, in this method, you can't control the size of the image. Therefore, sometimes it's better to use the following HTML syntax:  
```
<img src="link" alt="alternative text, shows when hovering" width= "" height= "">   
```
<img src="https://media.4-paws.org/1/e/d/6/1ed6da75afe37d82757142dc7c6633a532f53a7d/VIER%20PFOTEN_2019-03-15_001-2886x1999-1920x1330.jpg" alt="picture of dog" width="276" height="200">   


_Figure 2: A picture of a puppy as an example of how to insert an image with adjusted size._

#### 2.2.7. Code and Syntax Highlighting
Code blocks should be enclosed by lines containing three backticks (```) before and after the code.  
While this isn't part of the Markdown specification, some renderers, such as GitHub, support highlighting functions, allowing you to `highlight words` or sentences by enclosing them with a single backtick (`) before and after the word.

#### 2.2.8. Tables
Tables are not supported by standard Markdown, but they are supported by *Markdown Here*. To create tables, you use pipes (|) to separate columns and dashes (-) to separate rows. By using colons (:) before and/or after the dashes, you can change the alignment of the content within the table cells from left to center to right.

Apple|Bread|Milk
:-:|:-:|:-:
2$|3$|2.5$   

#### 2.2.9. Blockquotes
By placing a greater than symbol (>) in front of a sentence,  
> you can format the sentence as a blockquote.

#### 2.2.10. Inline HTML
Inline HTML refers to the use of HTML code within a Markdown document. HTML stands for "Hypertext Markup Language" and serves as the standard markup language for creating websites and web applications. It describes the structure and layout of a web page through the use of markup tags that instruct browsers on how to display and organize the content of a page.  
When you use Markdown, you essentially have the ability to integrate HTML tags into your text to create specific formatting or layouts that are not achievable with pure Markdown alone. This approach is called “inline HTML” because the HTML code is inserted directly into the Markdown text. HTML consists of various elements that are separated by tags, enclosed in angle brackets (<>), and may contain attributes that provide additional information about the element.  
For instance `<dl>` is used to start a definition list and `</dl>` to end one. Within this list one can add other tags like `<dt>` and `</dt>` to set the definition term. Within the HTML you should not use Markdown but better to use HTML tags, for instance `<strong>` und `</strong>` to write the text bold. 

<dl>  
    <dt>A definition list:</dt>
    <dd>Is something people use sometimes.</dd>
    <dt>Markdown in HTML:</dt>
    <dd>As **you** can *see*, Markdown does ~~not~~ work in HTML.</dd>
    <dd><u>Use</u> HTML <em>tags</em> <strong>instead!</strong></dd>
</dl>


# 3. Linux <a name="linux"></a> 
### 3.1. Introduction to Linux <a name="introductiontolinux"></a>
Linux is an operating system similar to Windows, which is integrated into various systems such as servers or computers. Its advantages include being open source, free of cost, offering high security, and providing high performance, especially on servers. To interact with Linux, one needs a **Unix shell**, a software environment that allows users to input commands. The Unix shell thus serves as a command-line interface (CLI). The most important types of Unix shells for us are the Bourne Shell (sh) and the Bourne-Again Shell (bash).  
To use the command line, a specific format is needed, where one typically has `<program name>[parameters][arguments]`. A parameter is an optional instruction that changes the behaviour of the program. Some examples of possible parameters are:
- `-l`: Provides a detailed list of files and directories.
- `-a`: Displays hidden files and directories as well.
- `-h`: Shows file sizes in a human-readable format (e.g. KB, MB, GB)
- `--output <filename>`: Specifies the output destination for the program's results or the processed data.

The output of a command is typically directed to the standard output of the shell, which is the screen displayed to the user.

### 3.2. Navigation <a name="navigation"></a>
Knowing the basics about paths and the most common commands to navigate through, create and manipulate files and folders is quite useful. 
There are relative and absolute paths. An absolute path specifies the exact location of a file or directory in the file system, starting from the root directory. A relative path specifies the location of a file or directory relative to the current working directory. It uses the current position in the file system as a reference point. This means that the relative path is shorter and more flexible, as it depends on the environment in which it is used.

The most important commands are as follows:
- `pwd`: Stands for "print working directory" and shows the current path.
- `ls`: Provides an overview of the contents of the current directory.
- `ls ./../../`: By adding two dots and a slash, you can view the content of the parent folder. Adding additional two dots and a slash allows you to access the parent folder of the parent folder, and so on.
- `ls ~/`: Lists the content of your home directory.
- `cd`: Sends you to your home directory.
- `cd <foldername>`: To change your location, use the cd command followed by the folder name.
- `cd ..`: Sends you one level up.
- `mkdir <foldername>`: Stands for "make directory". Create a new folder by typing the command followed by the desired folder name.
- `touch <filename>`: Creates an empty file.
- `cp <soure> <destination>`: Stands for "copy" and is used to copy files. Copied files can be renamed and moved into a folder.
- `cp -r <source> <destination>`: Copies a folder with its contents. 
- `rm <filename>`: Using the remove command followed by the file name deletes the file in the folder. Typing `rm -r <foldername>` deletes the folder and its contents.
- `mv <source> <destination>`: Used to move or rename files or folders. For example, `mv test_file renamed_test_file` renames a file. To move multiple files simultaneously, connect their names with the command `touch` followedd by the names of the file.  

One important feature in this context is globbing. When you want to apply the same command to several files, you can use a globbing pattern instead of explicitly writing all the filenames. This is done by using the asterisk (*) to replace none, one, or more characters, followed by the file extension (e.g. `*txt`).

### 3.3. Basic Commands <a name="basiccommands"></a>
Here are some other important commands:  
- `echo`: Used to output text or variable values to the screen.
- `>`: To redirect the output into a target file, use `> <destination>`. If you do not want to overwrite the content, use `>> <destination>` instead.
- `*.md`: Selects everything that ends with the extension ".md". 
- `head -n <filename>` or `tail -n <filename>`: Using either the head or tail command, you can get the first or last lines of a file. Specify the number after the command with `-n`.
- `cut -c`: Allows you to select characters horizontally. For example, `cut -c 1-10 <filename>` would print out the first 10 characters of each line in the file.
- `wc`: Stands for "word count" and can give you the number of words, lines or characters of a plain text file. For instance, use `wc -l <filename>` to count lines.
- `sort`: Sorts your file alphabetically or numerically.
- `grep <specific word> <filename>`: Finds all lines in the file that contain the specific word (case sensitive). Adding `-i` after the grep command makes the search case-insensitive.
- `tr X Y < <filename>`: Exchanges one character X for another Y and outputs the modified file.

# 4. Working with Data <a name="workingwithdata"></a>
## 4.1. Connect to HPCs <a name="connecttoHPCs"></a>
For a beginner it is quite challenging to understand how to access an HPC and how the remote access to the computer and server works.  
To access a High-Performance Computing system from your personal computer (PC), you typically use remote access protocols such as SSH (Secure Shell). Most HPC systems provide SSH access, which allows you to connect securely to the HPC system's command line interface from your PC. To do this, you need an SSH client installed on your PC (such as OpenSSH on Linux or macOS). 
We used ssh on a Mac with Linux as an operating system, thats why we used the following defined protocol:

`$ssh -l <lrz-Kennung> -p 122 CON-compute1.it1.bio.lmu.de`  
or  
`$ssh -p 122 <lrz-Kennung> @CON-compute1.it1.bio.lmu.de` 

Below I explain the ssh commmand line: 
- The dollar sign is not part of the code, it only indicates the beginning of the user input.
- `ssh`: This is the command-line tool used to establish the secure shell connection to the remote server.
- `-l <lrz-Kennung>`: The `-l` option is used to specify the username for the SSH connection. In this case, `<lrz-Kennung>` should be replaced with my personal LRZ username.
- `-p 122`: The `-p` option is used to specify the port number for the SSH connection. Here, it's set to port 122.
- `CON-compute1.it1.bio.lmu.de`: This is the hostname or IP address of the remote server. In this case, it is the compute node named "CON-compute1" within the "it1.bio.lmu.de" domain.  
An alternative method of accessing a computer is through remote control, where you can manage another computer over a network connection. However, this approach is not commonly used in HPC environments.

### 4.2. Work on an HPC <a name="workonanHPC"></a>
#### 4.2.1. Access
Once we've connected to the HPC system via SSH, the next step is to access files and directories. Here are some common methods:
- SFTP or FTP: SFTP (SSH File Transfer Protocol) and FTP (File Transfer Protocol) are commonly used for transferring files between a local computer and a remote server. SFTP is more secure as it encrypts both commands and data, while FTP may transmit data in plaintext. These protocols are typically used for read-only access or anonymous access to files and directories on the remote server.
- SMB (Samba): SMB refers to the Server Message Block protocol, which is commonly used for file sharing in Windows networks. When accessing shares directly on your host system from the HPC system, you can use the SMB protocol via Samba. The command to mount SMB shares is `mount -t smbfs`.
- Other Protocols: Additionally, other protocols such as NFS (Network File System), CIFS (Common Internet File System), and AFP (Apple Filing Protocol) may be used for accessing files and directories on remote servers. 

#### 4.2.2. Transfer
After accessing data, you can securely transfer it using SCP (Secure Copy), which is a command-line tool used for copying files between computers over a network. The syntax for using SCP is as follows: `$scp [OPTION] [user@]SRC_Host:]file1 [user@]Dest_Host:]file2`.  
This command is typically used to transfer files from a local computer to a remote one.  
Here's an example of using SCP to copy a file (fileA) from a local computer to a remote server (CON-compute.it1.bio.lmu.de) using port 122 and specifying the destination directory:  
`scp -p 122 fileA username@CON-compute.it1.bio.lmu.de://Destination/`  

#### 4.2.3. Check the Transferred Data
After transferring your data, it's essential to ensure that the transfer was successful and that the files arrived intact. Various methods can be employed to compare files and verify that the correct version has been transferred. During the copying process, individual bits may flip due to issues such as disconnected network connections, memory errors (ECC), or other factors. These changes can cause slight alterations to the file, potentially corrupting its contents. Even small changes in bits can result in significant differences in the file's contents. To prevent corrupted files, it's important to employ methods for checking the transferred data.
Here are some methods for checking the integrity of transferred files:
- Direct comparison: The simplest method involves comparing the contents of the transferred files directly to see if they are identical. This can be done using the `diff` command: `$ diff fileA fileB`. However, this method may not always work, especially when the files are transferred between remote systems.
- Checking file sizes: Another approach is to compare the sizes of the files using the `ls` command:
    ```
    $ ls -l fileA  
    $ ls -l fileB
    ```
    If the file sizes match, it indicates that the files are likely identical.
- Using hash functions: Hash functions, such as MD5 (Message Digest Algorithm 5), provide a reliable way to compare data. MD5 generates a fixed-size hash value (or signature) from the file's contents, which can be compared with the hash value of the original file. This ensures that even small changes to the file will result in a different hash value. The `md5sum` command can be used to calculate the MD5 hash of a file:
    ``` 
    $ md5sum fileA
    $ md5sum fileB  
    ```
It is also possible to only transfer changed or missing content. For that you can use the `Rsync` (Remote sync) command-line, it can transfer and synchronize files between directories, whether locally or over a network. Its primary advantage lies in its ability to transfer only the changed or missing content, significantly reducing transfer time and bandwidth usage.
Here's an overview of how Rsync works and how to use it:
- Basic usage: The syntax for using Rsync is straightforward: `rsync -avz source_directory/ destination_directory/`. 
This command synchronizes the contents of the source_directory with the destination_directory, ensuring that only the changed or missing files are transferred.
- Verbose output (-v): The `-v` option enables verbose output, allowing you to see detailed information about the files being transferred directly in the command-line interface.
- Archive mode (-a): The `-a` option, also known as the archive mode, ensures that Rsync operates recursively, preserving permissions, ownership, timestamps, symbolic links, and other attributes of the files and directories being transferred.
- Compression (-z): The `-z` option enables compression during the transfer, reducing network traffic and transfer time, especially over slower connections.
- Remote transfers: Rsync can also be used for transferring files to remote servers. For example: `rsync -p 122 -avz fileA ra46suz@CON-compute1.it1.bio.lmu.de://destination/`. This command transfers fileA to the remote server specified by the hostname CON-compute1.it1.bio.lmu.de, using port 122, and places it in the destination directory.
- Deleting remote files (--delete): To ensure that the destination directory exactly mirrors the source directory, you can use the `--delete` option. This tells Rsync to delete any files in the destination directory that are not present in the source directory.
- Include Checksums (--checksum): You can include checksum verification by using the `--checksum` option. This tells Rsync to compare checksums of files with identical sizes to ensure their integrity.

#### 4.2.4. Task: MD5 Checksum
In the couse I created a new directory: `mkdir -p /LETHE/Courses/cecilia`.  
After that, I exited the remote connection and created two identical files in a new directory. I then compared them by size using the `diff` and executed a MD5 checksum.
``` 
diff file1.txt file2.txt
ls -l file1.txt file2.txt
md5sum file1.txt file2.txt
```
Next I made a small change and saved it as a third file (file3.txt) and compared them again with diff and MD5 checksum:  
``` 
diff file1.txt file3.txt
ls -l file1.txt file3.txt
md5sum file1.txt file3.txt
```

Next I copied my file1 to the remote server into a new directory using `scp`:  
```
scp -P 122 file1.txt ra46suz@CON-compute1.it1.bio.lmu.de:/LETHE/Courses/cecilia/
```

and also the other two files but using `Rsync`:
```
rsync -avz -e "ssh -p 122" file2.txt file3.txt ra46suz@CON-compute1.it1.bio.lmu.de:/LETHE/Courses/cecilia/
```
and now again I compared them by size and MD5 checksum on the remote server. Once for the file1 and file2 and once for the file1 and file3 (I did not write out this step).
```
diff file1.txt file2.txt
ls -l file1.txt file2.txt
md5sum file1.txt file2.txt
```

### 4.3. Scripting <a name="scripting"></a>
Scripting is convenient for several reasons. Firstly, it allows us to automate repetitive tasks, saving time and effort in the long run. Additionally, scripting enables us to run tasks remotely, which makes it easier to manage and execute from any location. Moreover, it improves reproducibility by ensuring consistent results in different environments. Finally, scripting promotes code sharing and encourages collaboration and knowledge sharing. The first line of each skript must define the language in which the script is written. This is done using the shebang, a character sequence that apperars at the beginning of a script file. It indicates the absolute path to the interpreter that should be used to execute the script. In this case, **#!/bin/sh** specifies that the script should be interpreted by the Bourne shell (sh). This line tells the system what type of script it is and which software to use when running it. There are many different interpreters available for running scripts, including sh (Bourne shell), bash (Bourne Again shell), zsh (Z shell), ksh (Korn shell), as well as interpreters for other programming languages like Python and R.

To run a script, you can use the `sh` command followed by the path to the script file: 
```
$ sh ./my-script.sh
```
If you are denied permission you can use the following code: 
```
$ chmod +x my-script.sh
```
After setting the execute permission, you can run the script directly:
``` 
$ ./my_script
```
It is important to ensure that you're in the right directory when executing a script.

### 4.4. Syntax of Scripting <a name="syntaxofscripting"></a>
#### 4.4.1. Comments
To add comments that are not executed by the computer, you can use the hashtag (#). It is always beneficial to use comments to explain each step of your script.

#### 4.4.2. Variables
You can name a variable using the "=" sign. Variables can be declared and called again. Here's an example of how a simple script with a variable would look:
```
!/bin/sh
#This is a test script
name="Cecilia"
echo "Hello $name"
``` 
The output would be "Hello Cecilia".

#### 4.4.3. Loops
They are used to automate repetitive tasks. There are two main types of loops: **while loops** and **for loops**.
- For Loops: A for loop is used when the number of loop iterations is known in advance or when a loop needs to iterate over a sequence of elements. In a for loop, a counting variable is initialized, the loop condition is defined, and the counting variable is incremented or decremented in each loop iteration. For example:
    ```
    for i in range(5)
        echo(i)
    done
    ```
- While Loops: A while loop is used when the loop should continue to run as long as a specific condition is true. In a while loop, only the condition to be checked before each loop iteration is specified. For example:
    ```
    x = 0
    while x < 5:
        echo(x)
        x += 1 #add 1 to the counter
    done
    ```
#### 4.4.4. If Conditions
The "if" condition allows to execute a code block only if a specified condition is true. If the condition is true, the code inside the statement is executed, otherwise it skipps it.
Here's an example demonstrating the usage of "if," "elif," and "else":
```
x = 10
if x > 10:
    echo("x is greater than 10")
elif x < 10:
    echo("x is less than 10")
else:
    echo("x is equal to 10")
```

### 4.5. Task: BacGenome <a name="taskbacgenome"></a>
We split a microbial genome by the number of course participants and assigned each person one part. Our task was to create a script that creates two directories: "fasta" and "gff". Next, each participant copied their allocated files and decompressed all files with the ".gz" extension using the "gunzip" command.  

```
#!/bin/bash
#Author: Cecilia Siemens
#Script name: 12_files_cecilia_skript.sh (important for the SLURM task)

path="/LETHE/COURSES/hpc_course/data/bac_genomes/refseq/bacteria"
mkdir -p /LETHE/COURSES/hpc_course/Cecilia/fasta
mkdir -p /LETHE/COURSES/hpc_course/Cecilia/gff
#Directories have been created within the directory /LETHE/COURSES/hpc_course/Cecilia

while read -r line
do  
    echo $line
    cp ../../data/bac_genomes/refseq/bacteria/$line/*.fna.gz /LETHE/COURSES/hpc_course/Cecilia/fasta/
    cp ../../data/bac_genomes/refseq/bacteria/$line/*.gff.gz /LETHE/COURSES/hpc_course/Cecilia/gff/
done < /LETHE/COURSES/hpc_course/Cecilia/bac_genomes_cecilia
#The script reads through each line in the file bac_genomes_cecilia and copies all files with the extension .fna.gz into the fasta directory, and all files with the extension .gff.gz into the gff directory. The command done < indicates the end of the loop and specifies the input file for the loop operation.

gzip -d /LETHE/COURSES/hpc_course/Cecilia/fasta/*
gzip -d /LETHE/COURSES/hpc_course/Cecilia/gff/*
#It decompresses all .gz files within the fasta and gff directories using the gzip command.

echo "gzip is done"

```

# 5. SLURM <a name="slurm"></a>
### 5.1. Introduction to SLURM <a name="introductiontoslurm"></a>
SLURM, which stands for Simple Linux Utility for Resource Management, is a workload manager used to handle multiple processes simultaneously. The most important feature is the queue, which manages the cores and assigns jobs to the available CPUs. Jobs in the queue are given a priority and wait until the resources they need are available. If a person executes a command without using the queue, it will be executed immediately, creating an unfair environment for all other users and potentially stopping other processes.  
SLURM commands can also be included directly into a script when using #SBATCH: 

```
#!/bin/sh

#SBATCH --job-name=job1
#SBATCH --mem=10G
#SBATCH --cpus-per-task=10

#Insert the rest of the script here:
```
### 5.2. Basic SLURM Commands <a name="basicslurmcommands"></a>
Now, let's go over some basic SLURM commands:
#### 5.2.1. Checking available resources
- Checking current NODE free capacities: `htop`. This command displays a real-time view of system processes and resource usage on the compute nodes.
- Checking overall available NODES information:`sinfo`.
- Checking overall available capacity: 
    ```
    sinfo --Node \
    --Format="nodehost,cpusstate,cpusload,memory,allocmem,freemem" | 
    column -t
    ``` 
    This command shows detailed information about the overall available capacity of compute nodes, including CPU state, CPU load, memory allocation, and free memory.
- Checking the queue: `squeue`. This command displays the status of jobs in the SLURM queue, including their job ID, user, partition, state, and other details.

#### 5.2.2. Running Jobs
- General approach: `srun <COMMAND>` this command is used to run a specific command on the compute nodes.
- Specifying CPU allocation and max MEM usage: `srun echo -c 10 --mem 5G "Hello World"`. This command specifies the number of CPUs (-c) and maximum memory (--mem) to be allocated for the job.

#### 5.2.3. Running Jobs Non-Interactively
- Running jobs in the background: `srun echo "Hello World" &`. This command runs the job in the background by using "&" at the end of the command, allowing you to continue using the shell interactively.
- Submitting scripts to the queue: `sbatch ./myscript.sh`. This command submits a script (myscript.sh) to the SLURM queue for execution.

### 5.3. Task: SLURM <a name="taskslurm"></a>
For the task, each of us wrote an SBATCH script to execute our script designed for sorting and decompressing fasta and gff files. We ensured that our SBATCH script included a mechanism to print out the time it took for running the script, which we achieved using the `time` command.
```
#!/bin/bash
#sbatch script to execute my '12_files_cecilia_script.sh' (from the task with the fasta and gff files) and measure the time it takes to run.

#SBATCH --job-name=cecilia
#SBATCH --mem=5G  #The job requires 5 gigabytes of memory
#SBATCH --cpus-per-task=10 #The script needs 10 CPU cores

START=$(date +%s)
#Record the current time in seconds as the start time

./12_files_cecilia_skript.sh
#Run the script "12_files_cecilia_script.sh" that was used for the task with the fasta/gff files

END=$(date +%s)
#Record of the current time in seconds

DIFF=$(($END - $START)) 
#Calculate the difference between the end and start time to determine the total duration of the job

echo "It took $DIFF seconds"
exit 0 
```

# 6. Alignment Programs <a name="alignmentprograms"></a>
### 6.1. Introduction to Alignment Programs <a name="introductiontoalignmentprograms"></a>
Alignment programs are used to compare and analyze biological sequences, such as DNA, RNA, or protein sequences. They are important for tasks such as identifying or comparing species. Among the notable alignment programs are BLAST, VSEARCH, and the Needleman-Wunsch algorithm.
1. BLAST (Basic Local Alignment Search Tool) compares biological sequences against a vast database of known sequences. It uses an heuristic algorithms to rapidly identify similarities and potential homologous sequences. Unlike global alignment tools, which search for matches across the entire query sequence, BLAST uses a local alignment approach. This means that it compares sequences in smaller chunks, allowing for faster performance without sacrificing accuracy. There are several variants of BLAST, including BLASTn (for nucleotide sequences), BLASTp (for protein sequences), BLASTx (for translating nucleotide sequences into protein sequences before searching), and tBLASTn/tBLASTx (for comparing a protein sequence against a nucleotide database).
2. VSEARCH, on the other hand, is a global alignment tool because it compares the entire sequence. It is specifically built for metagenomic sequence analysis, boasting optimization for handling large datasets.
3. The Needleman-Wunsch algorithm is a programming algorithm used for global sequence alignment. It aligns two sequences by maximizing the similarity between them, accounting for gaps and mismatches.

### 6.2. Task: Aliscale <a name="taskaliscale"></a>
We wanted to use our newly acquired knowledge by comparing the three alignment programs. To accomplish this, we compared the runtime of the alignment process, considering the tool used, the query size, the database size, and the number of cores.  
In the first step, we were grouped into three groups: BLAST, VSEARCH, and Needleman-Wunsch.
I belonged to the BLAST group. In the first step, we compared various databases using either 1 or 10 cores, against our query sequence, while measuring the time taken to locate the query. We used the different numbers of databases: 10, 100, 1000, 10000, and 100000.
```
#!/bin/sh
#Setting the variables. $1 and $2 are arguments that should be specified in the terminal after the script name ./script.sh to indicate the different databases and cores that are used
    core=$1
    database=$2
#Set the path where the databases are located
    pathdatabase=/LETHE/COURSES/hpc_course/Cecilia/Aliscale/$2.fa
#Save the current date into a variable
    #date1=$(date +%s) Würde die Zeit in Sekunden angeben
    date1=$(date +%s%N)
#Perform the BLAST search
    blastn -query 1.fa -num_threads $core -db $pathdatabase
#Save the current time for a second time and store it in a variable
    date2=$(date +%s%N)
#Calculate the time difference between date1 and date2
    timediff=$(expr $date2 - $date1)
#Calculate the time difference from nanoseconds to milliseconds. Expr shows that there is a calculation to do
    timediff_ms=$(expr $timediff / 1000000)
#Display the time passed
    echo "time passed"
    echo "$timediff_ms" 
#Display the BLAST details including core count, database, and time taken
echo "BLAST, $core, $database, $timediff_ms"
```

My values were as follows:  
blast 1 10 0.081  
blast 1 100 0.101  
blast 1 1000 0.233  
blast 1 10000 0.311  
blast 1 100000 0.834  
blast 10 10 0.057  
blast 10 100 0.096  
blast 10 1000 0.198  
blast 10 10000 0.225  
blast 10 100000 0.361  

In the second step, each person from the three groups copied their values into a text file in the directory "aliscale_speeds". Then, each person created a code that merges the text files from the "aliscale_speeds" folder into a single file in their directory using the `cat` command.
```
#!/bin/sh
#Merging the .txt files from the directory into my own text file ../Cecilia/Merge.txt
cat /LETHE/COURSES/hpc_course/aliscale_speeds/*.txt > /LETHE/COURSES/hpc_course/Cecilia/Merge.txt
``` 
In the third step, a group graph was created from the merged files using a Python package:
```
#!/bin/sh
python ./plot_speeds.py Merge.txt Gruppengraph.png 
```
The ./plot_speeds.py script has been provided by Daniel and was used to create the graph "Groupgraph.png" from the data in the text file "Merge.txt".

The following is the script we used to create the graph, developed by Daniel. There was a slight change: the graph needed to be logarithmical on the y-axis, so plt.yscale(log) had to be added.

```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import argparse
# read argument for the input file

parser = argparse.ArgumentParser(description='Plot the speed of the program, the format should be: program cores dataset time, separated by a space')
parser.add_argument('input_file', metavar='input_file', type=str,
                    help='the input file')
parser.add_argument('output_file', metavar='output_file', type=str,
                    help='the output file') 

args = parser.parse_args()

df = pd.read_csv(args.input_file, sep=" ", header=None)

df.columns = ["program", "cores", "dataset", "time"]

# plot with the line and the points

# sns.set(style="whitegrid")
ax = sns.lineplot(x="dataset", y="time", hue="program", size="cores", data=df)
ax = sns.scatterplot(x="dataset", y="time", hue="program",
                     data=df, size="cores", legend=False)
ax.set(xlabel='Dataset size', ylabel='Time (s)')
plt.title("AliScale: execution time of the alignment programs")
plt.xscale("log")
plt.yscale("log")

plt.savefig(args.output_file)
```
With the help of Daniel's script, the following graph was generated.
[![Plot-cecilia.png](https://i.postimg.cc/yNXF3Nr6/Plot-cecilia.png)](https://postimg.cc/d737zJYg)  
_Figure 3: Comparison of the time, the BLAST program needed for different datasets using either 1 or 10 cores._  

The x-axis represents the database size with increments of 10, 100, 1000, 10000, and 100000, while the y-axis represents the time taken by BLAST to find the matching query sequence in our database. Additionally, there is differentiation between 1 (thin line) and 10 (thick line) cores.
It can be observed that as the database size increases, the time also increases. With one core, the time taken initially is under 0.1 seconds, rising to just over 0.8 seconds for the largest database. With 10 cores, this increase is less pronounced, the time increases from under 0.1 seconds to just about 0.36 seconds.
These results were as we expected them to be since the size of the database directly correlates with the time required for the program to locate the sequence. Additionally, with a larger number of cores, the time should not increase as much as with only one core, as cores enable parallel processing, providing higher processing power and better multitasking capabilities.

As one can see below, the group graph looks different compared to my BLAST graph:  
[![Gruppengraph.png](https://i.postimg.cc/VLC4Lz1v/Gruppengraph.png)](https://postimg.cc/QHjcfGFZ)  
_Figure 4: Comparison of the execution times of the three alignment programs._

The x- and y-values display the same information as the BLAST graph (compare figure 3), but here we can see the other groups as well. BLAST is shown in blue, Needleman-Wunsch in orange, and VSEARCH in green. The thin lines represent core=1, while the thick lines represent core=10.
It can be observed that initially all three programs require less than 0.1 seconds to find a sequence in the first set of databases. However, it quickly becomes apparent that the longest execution time was recorded for the Needleman-Wunsch group, taking over 500 seconds to discover the target sequence in the largest database set. This measurement was conducted using only one core.  
Conversely, for VSEARCH, the execution time started at its lowest, around 0.05 seconds. Even with 10<sup>2</sup> databases, the times remained roughly the same. As the number of databases increased to 10<sup>3</sup>, VSEARCH (core=10) still remained the lowest compared to the others with 10 cores, at around 0.1 seconds, while at core=1, VSEARCH had a time of 0.2 seconds, which was approximately equal to BLAST. However, as the database size increased, the time for VSEARCH increased to higher values compared to BLAST. For instance, at 10<sup>5</sup> databases, the time for VSEARCH at core=1 increased to around 17 seconds and at core=10 to 3 seconds. In contrast, BLAST maintained times below 0.1 seconds at core=1 and below 0.4 seconds at core=10, even with database sizes up to 10<sup>5</sup>.  
These results align with our expectations, as VSEARCH is expected to perform quickly and accurately on smaller databases due to its global alignment approach. VSEARCH is therefore most practical when dealing with small datasets but requiring more precise results. This is evident in the graph, where the program is initially fast with smaller datasets but experiences increased execution times with larger datasets. For BLAST, the local alignment search enables it to quickly find a match even in larger datasets. However, the results may not be as precise as those from VSEARCH since only smaller segments of the sequence are compared with the target sequence. Nevertheless, the results are generally accurate enough for most purposes, which is why BLAST remains popular—fast yet relatively accurate. This is also reflected in the graph, where although the time increases with dataset size, it does so less compared to the other programs, and even with large datasets, the program can still deliver quick results. Needleman-Wunsch performs best with few sequences and small databases, providing very accurate results. This can be seen in the graph, where the time increases almost linearly, indicating that this program is not well-suited for large datasets.

# 7. Containerization and Dockers <a name="containerizationanddockers"></a>
### 7.1. Introduction to Containerization and Dockers <a name="introductiontocontainerizationanddockers"></a>
In a multi-user environment, it's useful to have administrators with administrative rights who are authorized to perform updates and download packages to ensure security. If a user requires a tool or package that is not installed and cannot be installed by a regular user, containerization becomes relevant. Containers create an user space isolated from the rest of the computer.  
The benefits of containerization include:
- Reproducibility: Containers capture the entire software environment, making it easy to reproduce experiments.
- Portability: They can run consistently across various platforms, from local machines to HPC clusters.
- Isolation: Containers isolate applications, preventing conflicts between different software dependencies.

A Docker setup always includes:  
- The Docker Daemon: A background service that manages Docker objects such as images, containers, networks, and volumes on the host operating system.
- The Docker Command Line Interface (CLI): A user-friendly tool for interacting with the Docker daemon via commands entered in a terminal or command prompt.
- Docker images: They are read-only templates containing all the necessary files and dependencies to run a software application. On Docker Hub, users can find, store, and share Docker images, making it a central repository for Docker images.
- Docker containers: They are lightweight, portable, and self-contained runtime environments created from Docker images. Each container runs as an isolated process on the host system and includes its own file system, networking, and runtime resources.

The main commands are `docker run` and `docker pull`, for example:
```
docker pull [Name of the application]
docker run [Parameters] [Application]
```
An alternative to Docker is Singularity, a more secure container system. 

### 7.2. Task: Diamond <a name="taskdiamond"></a>
1. What is Diamond?
Diamond is a versatile program used to align DNA reads or protein sequences with a protein reference database. Its main highlights are its impressive speed enhancements, boasting speeds nearly 20,000 times faster than BLAST, without sacrificing sensitivity. This efficiency is achieved through the use of heuristic search algorithms. Diamond is suitable for a variety of tasks, including protein-protein and DNA-protein searches, making it adaptable to different research needs. It can handle both short reads and longer sequences, providing flexibility in data analysis. Additionally, Diamond has low resource requirements, allowing it to run smoothly on standard desktops or laptops. It supports multiple output formats, including those compatible with BLAST, enhancing its compatibility with existing workflows.

2. Learn about pegi3s bioinformatics docker images project  
PEGI3S (Parallel Execution of Genomic Inference of Transcript Isoform Splicing) offers a fast and efficient method for identifying alternative splicing events and characterizing isoform diversity in transcriptome data. PEGI3S/PSS-FS focuses specifically on detecting alternative splicing sites in fragile site regions of the genome, known for their high genomic instability.

3. Install Diamond using docker and run the 1.fa file against the 100000.fa file  
4. you may need to translate the nucleotides into proteins, you can try to use a tool from pegi3s bioinformatics docker project (you may need to check into the emboss tool)

    In the first step, Diamond is installed using the command: `docker pull pegi3s/pss-fs`. 
    Then, the transeq command, which is part of the Emboss package, is used to translate nucleotide sequences into amino acid sequences. The input file used is 100000.fa, and the output file is named 100000.pep.

    ```
    ra46suz@LMBIDP1-LXKEL01:/LETHE/COURSES/hpc_course/Cecilia/2.Skript_container$ transeq
    Translate nucleic acid sequences
    Input nucleotide sequence(s): 100000.fa
    protein output sequence(s) [linum_alpinum.pep]: 100000.pep
    ra46suz@LMBIDP1-LXKEL01:/LETHE/COURSES/hpc_course/Cecilia/2.Skript_container$ 
    ```

    In the third step, the Diamond-blastx command is executed. This is done by running the docker run command with the pegi3s/diamond Docker image. The amino acid sequence in the file 1.fa is compared with that in the file 10000.pep.

    ```
    #!/bin/sh
    docker run --rm -v /LETHE/COURSES/hpc_course/Cecilia/2.Skript_container:/data pegi3s/diamond blastx --query /data/1.fa --db /data/100000.pep
    ```
    Here, the `-v` option connects the directory `ra46suz@LMBIDP1-LXKEL01:/LETHE/COURSES/hpc_course/Cecilia/2.Skript_container` with the /data directory in the Docker container, enabling file exchange between the host and container. pegi3s/diamond refers to the name of the Docker image containing the Diamond-Blastx algorithm. The `blastx` command, executed within the container, utilizes protein-protein database search. The `--query /data/1.fa` option specifies the path to the input file for the blastx command within the container. The file 1.fa is located in the /data directory within the container, which was previously connected to the host directory. The `--db /data/100000.pep` option specifies the path to the database file used for the Blastx search.  
    The result indicates a match with a similarity of 93% with the species Linum_alpinum.

# 8. Project BacGenStat <a name="projectbacgenstat"></a>
Our latest project, the BacGen project, focuses on comparing the correlation of the GC/AT content and genome size in different bacterial genomes.  
For the task, we have a vast dataset containing different genera with their genomes stored in FASTA files and their information about taxonomy and genes stored in GFF files. From these genomes, we aim to calculate the GC content of individual phyla and subsequently generate graphs for comparison. To accomplish this, I used two scripts, with the second one executing the first one (bac.gen.sh). Firstly, the number of genes present in the genome is counted, followed by the extraction of taxonomy information. Next, the number of nucleotides is counted, and the GC ratio is calculated. Finally, the results are saved in a file named data.txt, which includes the GC content, number of genes, and the corresponding phylum, for example: 0.039 12597 Bacillota. In the final step, we create various plots using Python via Linux to visualize the GC ratio of different phyla in correlation with their genome size.

The first script is shown below:

```
#!/bin/bash

#SBATCH --job-name=cecilia
#SBATCH --mem=5G 
#SBATCH --cpus-per-task=1

#Assign the value of the first argument (genome name) to the variable genome
genome=$1

#Calculating the number of genes in the genome. "grep -Ec" outputs the number of lines containing the CDS
number=$(grep -Ec "CDS" ./gff/${genome}.gff)

#Extracting the species by searching for the line containing the pattern "##species" in the gff file and removing all non-digits (tr -cd '[:digit:]')
id=$(grep '^##species' ./gff/${genome}.gff | head -1 | tr -cd '[:digit:]')

#Receiving taxonomy information for the species using a docker container named `ncbi/edirect`. Within the docker container taxonomy information can be accessed
taxonomy=$(docker run --rm ncbi/edirect /bin/bash -c "efetch -db taxonomy -id $id -format xml | xtract -pattern Taxon -block '*/Taxon' -tab '\n' -element Rank,ScientificName | grep '^phylum' | cut -d$'\t' -f2 | tr -s '\n'")

#Counting the occurrences of A, T, G, and C
AT=$(grep -v ">" ./fasta/${genome}.fna | grep -Eo "A|T" | wc -l)
GC=$(grep -v ">" ./fasta/${genome}.fna | grep -Eo "G|C" | wc -l)

#Calculating the ratio of the GC content
GCratio=$(echo "scale=3; $GC/($GC+$AT)" | bc)

#Saving the calculated values in a file
echo "$GCratio, $number, $taxonomy" >> "./cache/data_${genome}.txt"
```

The following main script executes the first script repeatedly until every genome is analyzed.

```
#!/bin/bash

#SBATCH --job-name=cecilia
#SBATCH --mem=5G
#SBATCH --cpus-per-task=2

echo "Start scripting"

#Create a cache directory if it doesn't exist
mkdir -p ./cache

#Generate a list of genomes that have not been processed yet by checking the cache
genomes_to_process=()
for genome_path in fasta/*.fna; do
    genome=$(basename "$genome_path" .fna)
    if [[ ! -f "./cache/data_${genome}.txt" ]]; then
        genomes_to_process+=("$genome")
    fi
done

#Count the total number of genomes to process
total=${#genomes_to_process[@]}
echo "Total genomes to process: $total"

#Initialize a counter for the current genome being processed
current=0

#Loop to go through all the genomes sequentially
for genome in "${genomes_to_process[@]}"
do
    #Increment the current counter
    ((current++))
    #Run the processing script for each genome
    sh ./bac.gen.sh "$genome"
    echo "Processed $current out of $total genomes."
done

#Save all the data files into one
cat ./cache/data_*.txt > data.txt

echo "All genomes are processed."
```  
Finally, to create different graphs, Python is executed via Linux. This involves creating a file with the .ipynb extension and installing Python. Subsequently, you have a Python interface where you can input commands into boxes.  
The plots are created with the following script, based on the one we got from Daniel. 
``` 
#Import
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

#Import the table
df = pd.read_csv("data.txt", sep="|", header=None)
d = df[0].str.split(" ", expand=True, n=4)
d.columns = ["gc", "genes", "phylum", "x"]

#Select the non-empty "x" column data from the DateFrame "d" and save them in the DataFrame "non_empty_x"
non_empty_x = d[d['x'].notna()]

#This line removes all commas in the "gc" column and then converts the values to floats
d.gc = d.gc.str.rstrip(',').astype(float)

#This line removes all commas in the "genes" column and then converts the values to integers
d.genes = d.genes.str.replace(',', '').astype(int)

#Count the frequency of each phylum in the "phylum" column and store it in the variable phylum_counts
phylum_counts = d['phylum'].value_counts()

#Converting the phyla into a sorted list
sorted_phyla = phylum_counts.index.tolist()

g = sns.relplot(data=d, x="genes", y="gc", hue="phylum", hue_order=sorted_phyla, legend=False, aspect=1.25, alpha=0.4, col="phylum", col_order=sorted_phyla, height=1.75, col_wrap=6)
plt.xscale("log")
g.set_titles("{col_name}")

#x-axis: represents the gene count
#y-axis: represents the GC content
#hue: dots are colored based on the phylum
#legend=false: means no legend is displayed
#aspect: aspect ratio of individual plots
#alpha: transparency of the dots
#col: data is divided by phylum, each phylum has its own subplot
#col_wrap: number of subplots per row
```

The script created the following plots, the Y-axis represents the GC content, while the X-axis represents the number of genes.

[![Bildschirm-foto-2024-04-03-um-23-59-02.png](https://i.postimg.cc/QtRd598g/Bildschirm-foto-2024-04-03-um-23-59-02.png)](https://postimg.cc/Q9JDZMWV)
_Figure 5: Multiple plots show the correlation between GC ratio (Y-axis) and genome size (X-axis) across various phyla._

As shown in the plots, there is a partial correlation between the GC content and the number of genes. A positive correlation is particularly noticeable in Pseudomonadota and Actinomycetota. Our expectation would be that with an increasing number of genes, the relative GC content would also increase. This is because G and C nucleotides form three hydrogen bonds, making them more stable compared to A and T, which only form two hydrogen bonds. This correlation is also slightly noticeable in Bacteriodota. However, for the other phyla, it is challenging to identify a trend due to the smaller sample size, with mostly just assimilations of points being observed."

# 9. Personal Conclusion <a name="personalconclusion"></a>
Overall, I enjoyed the module and think it provided me with a solid foundation in computer/scripting skills. I think it's important to learn the basics properly so that one can then acquire additional content and skills. Despite the short duration, I think that we gained a good overview of the fundamentals. Simply being familiar with the terminology and knowing how to find solutions to my problems is valuable knowledge.
One aspect I particularly appreciated was the emphasis on independent work, which led to individual solutions and scripts. This forced us to quickly learn how to tackle problems on our own and effectively handle mistakes. Additionally, I found it beneficial that we always covered theory at the beginning of each session, providing context for the practical exercises. The integration of biology right from the start was also beneficial. It demonstrated the practical applications of scripting and HPCs in biological research.  
As a suggestion for improvement, I recommend including a tutorial on accessing the HPC from personal computers while early in the course. While I was able to figure it out independently after the course was over, having this knowledge from the start would have been quite helpful for post-class work and understanding.
Overall, I was pleasantly surprised and found the module to be well-executed and useful.
