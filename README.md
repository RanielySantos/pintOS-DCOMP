# pintOS-DCOMP
Pintos is an educational operating system for the x86. Pintos was developed for Stanford's CS 140 operating systems course.

Official website of Pintos-OS is [pintos-os.org](pintos-os.org).
To know more about the operating system and projects related to it, visit [http://courses.mpi-sws.org/os-ss13/assignments/pintos/pintos.html](http://courses.mpi-sws.org/os-ss13/assignments/pintos/pintos.html).

This version of Pintos-OS is froked from **git://pintos-os.org/pintos-anon**.
You can also view the Stanford git repository of Pintos-OS using their web CGI [http://pintos-os.org/cgi-bin/gitweb.cgi](http://pintos-os.org/cgi-bin/gitweb.cgi).

## Getting Started

* Start by cloning the code base to your machine. This will clone both branches and checkout to `master` branch. 
```
git clone https://github.com/RanielySantos/pintOS-DCOMP.git
```

## Configure
* Baixe o emulador QEMU no terminal
Following these steps will configure the operating system to use QEMU for emulation for linux systems.

* Navigate to `<nome da pasta clonada pelo git>/src/threads`, open `Make.vars` in a text editor and change line 7 to `SIMULATOR = --qemu`.
* Now navigate to `<nome da pasta clonada pelo git>/src/utils` and edit `pintos-gdb` by changing the line 4 to `GDBMACROS=../misc/gdb-macros`.
* In the same directory, edit the file `pintos` by changing:
	- Line 103 to `$sim = "qemu" if !defined $sim;`
	- Linha 257: Colocar todo o diretório em 'kernel.bin'. Exemplo: "/home/raniely/Downloads/pintOS-DCOMP/src/threads/build/kernel.bin"
	- Line 621 to `my (@cmd) = ('qemu-system-x86_64');`
* Modifique o arquivo Pintos.pm, na linha 362 coloque todo o diretório onde está o "loader.bin". Exemplo: "/home/raniely/Downloads/pintOS-DCOMP/src/threads/build/loader.bin"
* Modify `squish-pty.c` file by commenting
	- Line 10
	- Line 288-293 (both inclusive)
* Comment Line 11 in `squish-unix.c`

## Build
Before building the system, make sure to add the path to `pintos` in the `PATH` variable so that tests can be run as soon as the system is built. You can do so by adding this line in the '~/.bashrc' file.
```
Abra o terminal na área de trabalho, digite "gedit .bashrc". Vai abrir um editor de texto, aí faça o comando abaixo e depois salve.
export PATH="<path to directory>/<nome da pasta clonada pelo git>/src/utils:$PATH"
```

* Change the directory to `<nome da pasta clonada pelo git>/src/utils` and run `make`. This will compile the utilities in the folder.
* Navigate to `<nome da pasta clonada pelo git>/src/threads` and run `make`. This will compile the kernel and make a new directory `build` in the current directory.

## Run
You can check if the Pintos-OS is installed properly by running the following command in the `<nome da pasta clonada pelo git>/src/utils` directory.
Depois de estar no diretório, execute o comando abaixo:```
./pintos run alarm-multiple
Se aparecer uma janela do qemu, executando várias linhas de comando, então a configuração está correta.
```
