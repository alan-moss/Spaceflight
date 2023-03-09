# File Ingest Verify

This script compares all file names of two folders/directories against one another and returns the intersection of the two directories. The intended use case for this script it to compare **FC**, **NX**, and **Ground** directories in order to save storage space onboard the spacecraft.  
> Input: the names of two txt files  
> Output: txt file containing the intersection of the txt files  

## Requirements
### Python
- This script is written in python and was tested using Python 3.10
### Text files
This script requires two txt files to compare against one another. In order to create a text file containing a list of all filenames within a directory, open a terminal or powershell window, cd into the chosen directory, and enter the following command:
> **`ls > filename.txt`**

 Where *'filename.txt'* is the desired name of the output file.

This will produce a text file containing every file name within the current directory on a new line, e.g.

**`20220718_adcs_high200000.mtc`**  
**`20220718_adcs_high200001.mtc`**  
**`20220718_adcs_high200002.mtc`**  

If you prefer to include file permissions or file paths in your text file, you can do in Linux using the following commands:  

*With file permissions:*  
>**`ll > filename.txt`**  

**`-rw-rw-r-- 1 astroops5 astroops5  501 May 26  2022 20220526_df.txt`**  
**`-rw-rw-r-- 1 astroops5 astroops5  979 May 26  2022 20220526_ps.txt`**  
**`-rw-rw-r-- 1 astroops5 astroops5 1.6K May 26  2022 20220526_top.txt`**  

*With file path:*  
>**`ls -d "$PWD"/* > filename.txt`**  

**`/mnt/shared/tlm_store/backorbit/20220527_power00000.mtc`**  
**`/mnt/shared/tlm_store/backorbit/20220527_power00001.mtc`**  
**`/mnt/shared/tlm_store/backorbit/20220527_power00002.mtc`**  

This script will function properly in either case, as it gathers the *last string* on each line, using either a blank space or a forward slash as a string delimiter.


## Running the script  

In order to run this script, the two text files that are to be compared must be placed in the same directory the file_ingest_verify.py script is located.  

![Directory](https://github.com/alan-moss/Spaceflight/blob/main/MD_Images/file_ingest_verify_5.png)  

Below you can see the contents of each text file. Notice that there are five matching filenames.  

![File 1](https://github.com/alan-moss/Spaceflight/blob/main/MD_Images/file_ingest_verify_6.png)  
![File 2](https://github.com/alan-moss/Spaceflight/blob/main/MD_Images/file_ingest_verify_7.png)  

### Linux  
To run the script in Linux with Python 3+ installed, enter the following:  
>**python3 file_ingest_verify.py**  

Enter the name you would like your output file to be called, in addition to each file to be compared.  
>**NOTE**: if you enter a name for the output file that already exists within the directory, that file's contents will be overwritten.  


This program will continue to run until the user exits by typing "2" when prompted. A full run of the program can be seen below:  

![Run](https://github.com/alan-moss/Spaceflight/blob/main/MD_Images/file_ingest_verify_8.png)  

You may print the contents of the output file using the "cat" command, or you may go into edit mode using "nano".  

**Cat**:  
![Cat](https://github.com/alan-moss/Spaceflight/blob/main/MD_Images/file_ingest_verify_9.png)  

**Nano**:  
![Nano](https://github.com/alan-moss/Spaceflight/blob/main/MD_Images/file_ingest_verify_10.png)  

### Windows
To run this script on Windows with Python 3+ installed (and Python 3+ as first python environment in PATH), enter the following:  
>**python file_ingest_verify.py**  

Follow the prompts until you have exited the program. The best way to view the output file is by opening it with Notepad. This may be done using the following command:  
> **start notepad filename.txt**  

Where "filename.txt" is the name of the output file.  

![Windows_run](https://github.com/alan-moss/Spaceflight/blob/main/MD_Images/file_ingest_verify_4.png)  
