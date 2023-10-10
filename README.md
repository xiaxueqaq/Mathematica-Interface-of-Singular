# Mathematica-Interface-of-Singular
This is a project enabling Mathematica Users to call Singular commands. The interface was originally written by Manuel Kauers and Viktor Levandovskyy. This project modified the code so it can be executed with Windows 10 + WSL now (we assume Singular is installed under WSL). You may find the original version I based on here: https://www.risc.jku.at/research/combinat/software/Singular/.
But a more recent version is also available at http://www.kauers.de/software.html.

Here are the different aspects of this project:
1. In Windows 10, there is a Linux subsystem in it(WSL) and Singular is installed with the subsystem now (instead of Cygwin). I modified the package to call "wsl Singular" and translate the file system between Windows and WSL so the package will work properly.
2. The output of minAssGTZ and primdecGTZ seems to be wrongly parsed, probably because Singular changes the way it writes objects to files. I fix this in the modified package.
3. Also, somehow Singular will break the line when writing an integer to files, which adding an extra NULL in the output of Saturation. This is fixed now.
4. I change to way that Mathematica calls Singular (Run[] -> ReadList[]) so there won't be blinking prompt windows anymore. The system call is totally silent and invisible to the users now.
5. I add two global variable "LastSingularSessionTime" and "TotalSingularSessionTime" to record the CPU time (in milliseconds) used by Singular.

The new package is tested with Windows 10 + WSL 2 (Ubuntu 22.04) + Singular 4.2.1 + Mathematica 12, and all the functions seem to be working correctly.

You may find demos at https://www3.risc.jku.at/research/combinat/software/Singular/demo.nb and https://www3.risc.jku.at/research/combinat/software/Singular/demo.nb.pdf


# Install
1. Copy Singular.m to somewhere Mathematica can find. You may type command `$Path` in a new notebook to see the default paths that Mathematica looks for packages.
2. Use command ``Needs["Singular`"]`` to import the package.

Notice: This is only an interface, you need to install the Singular yourself. In Windows 10 + WSL, this can be done by `bash sudo apt-get install singular`. For information about Singular, please refer to the official website https://www.singular.uni-kl.de/.
