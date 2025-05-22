# LAPORAN TUGAS
## MATAKULIAH SISTEM OPERASI
### Fork : Parent - Child Process
Dosen Pengampu:

**Dr. Ferry Astika Saputra ST, M.Sc**

Disusun Oleh:

**Nauril Putri Hadining Tyas (3124521012)**

**PROGRAM STUDI D3 TEKNIK INFORMATIKA PSDKU LAMONGAN**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**

    

  fork() adalah sebuah system call atau fungsi khusus yang digunakan dalam sistem operasi mirip Unix (seperti Linux dan macOS) untuk membuat proses baru. Proses yang membuat proses baru ini disebut proses induk (parent process), dan proses yang baru dibuat disebut proses anak (child process). Proses anak ini pada dasarnya adalah salinan dari proses induk, dengan ruang alamat dan status eksekusi yang hampir identik.

  Setelah fork() dipanggil, baik proses induk maupun proses anak akan melanjutkan eksekusi dari titik yang sama dalam kode program. Proses induk dapat menggunakan nilai kembalian dari fork() untuk membedakan antara dirinya dan proses anak. Pada proses anak, fork() mengembalikan nilai 0, sedangkan pada proses induk, fork() mengembalikan Process ID (PID) dari proses anak yang baru dibuat. Jika terjadi kesalahan saat membuat proses anak, fork() akan mengembalikan nilai negatif.  
```
./ $fork01
```
![fork1](https://github.com/Naurilputri/SisOpe-2025/blob/main/screenshots/fork01.png)  
```
using namespace std;

#include <iostream>
#include <sys/types.h>
#include <unistd.h>


/* getpid() adalah system call yg dideklarasikan pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t mypid;
	uid_t myuid;
	for (int i = 0; i < 3; i++) {
		mypid = getpid();
		cout << "I am process " << mypid << endl;
		cout << "My parent process ID is " << getppid() << endl;
		cout << "The owner of this process has uid " << getuid()
	<< endl;
/* sleep adalah system call atau fungsi library
yang menghentikan proses ini dalam detik
*/
	sleep(3);
	}
return 0;
}

```
penjelasan fork01:  
Kode fork01.cpp hanya mencetak informasi tentang proses yang sedang berjalan, dan tidak membuat proses baru. Karena kode ini tidak menggunakan fork(), pohon prosesnya sangat sederhana dan hanya ada satu proses yang berjalan, yaitu proses utama yang menjalankan kode ini.  

```
[Proses Utama] (PID: ..., PPID: ...)


```
$ ./fork02
```
#include <iostream>
#include <sys/types.h>
#include <unistd.h>
using namespace std;


/* getpid() dan fork() adalah system call yg dideklarasikan
pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t childpid;
	int x = 5;
	childpid = fork();

	while (1) {
		cout << "This is process ID" << getpid() << endl;
		cout << "In this process the value of x becomes " << x << endl;	
		sleep(2);
		x++;
	}
	return 0;
}
```
![fork2](https://github.com/Naurilputri/SisOpe-2025/blob/main/screenshots_fork/fork02.png)  
```
                                  [Proses Utama] (PID: ..., PPID: ...)
                                          |
                                          | fork()
                                          |
                        --------------------------------------
                        |                                    |
            [Proses Induk] (PID: ..., PPID: ...)   [Proses Anak] (PID: ..., PPID: ...)
                        |                                    |
                        | (Loop Tak Terbatas)                | (Loop Tak Terbatas)
                        |                                    |
                        | ... (Terus Berjalan)               | ... (Terus Berjalan)
```
penjelasan fork02:  
Kode fork02.cpp punya loop while (1), yang artinya dia akan terus berjalan tanpa henti diulang-ulang terus setiap 2 detik, dengan nilai x yang terus bertambah. Jadi, kalau kita jalankan kode ini, outputnya akan terus muncul di layar sampai kita menghentikannya secara manual.  
  
```
$ ./fork03
```
#include <iostream>
using namespace std;
#include <sys/types.h>
#include <unistd.h>


/* getpid() dan fork() adalah system call yg dideklarasikan
pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t childpid;
	childpid = fork();
	for (int i = 0; i < 5; i++) {
		cout << "This is process " << getpid() << endl;
		sleep(2);
	}
	return 0;
}
```
![fork3](https://github.com/Naurilputri/SisOpe-2025/blob/main/screenshots_fork/fork03.png)  
```
                                  [Proses Utama (fork03)] (PID: ..., PPID: ...)
                                          |
                                          | fork()
                                          |
                        --------------------------------------
                        |                                    |
            [Proses Induk (fork03)] (PID: ..., PPID: ...)   [Proses Anak (fork03)] (PID: ..., PPID: ...)
                        |                                    |
                        | (Loop 5 kali)                       | (Loop 5 kali)
                        |                                    |
                        | (Selesai)                           | (Selesai)
```
penjelasan fork03:  
Karena ada fork() dan loop for, outputnya akan bercabang dan diulang. Jadi, outputnya akan ada 10 baris, 5 baris dari induk dan 5 baris dari anak, dengan jeda 2 detik antar baris.  

```
$ ./fork04
```
#include <iostream>
using namespace std;
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>
/* pid_t fork() dideklarasikan pada unistd.h.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/

int main(void) {
	pid_t child_pid;
	int status;
	pid_t wait_result;
	child_pid = fork();
	if (child_pid == 0) {
		/* kode ini hanya dieksekusi proses child */
		cout << "I am a child and my pid = " << getpid() << endl;
		cout << "My parent is " << getppid() << endl;
		/* keluar if akan menghentikan hanya proses child */
	}
	else if (child_pid > 0) {
		/* kode ini hanya mengeksekusi proses parent */
		cout << "I am the parent and my pid = " << getpid() << endl;
		cout << "My child has pid = " << child_pid << endl;
	}
	else {
		cout << "The fork system call failed to create a new process" << endl;
		exit(1);
	}
		/* kode ini dieksekusi baik oleh proses parent dan child */
		cout << "I am a happy, healthy process and my pid = " << getpid() << endl;
		if (child_pid == 0) {
		/* kode ini hanya dieksekusi oleh proses child */
		cout << "I am a child and I am quitting work now!"<< endl;
	}
	else {
		/* kode ini hanya dieksekusi oleh proses parent */
		cout << "I am a parent and I am going to wait for my child" << endl;
	do {
		/* parent menunggu sinyal SIGCHLD mengirim tanda bahwa proses child diterminasi */
		wait_result = wait(&status);
	} while (wait_result != child_pid);
		cout << "I am a parent and I am quitting." << endl;
	}
	return 0;
}
```
![fork4](https://github.com/Naurilputri/SisOpe-2025/blob/main/screenshots_fork/fork04.png)  
```
                                  [Proses Utama (fork04)] (PID: ..., PPID: ...)
                                          |
                                          | fork()
                                          |
                        --------------------------------------
                        |                                    |
            [Proses Induk (fork04)] (PID: ..., PPID: ...)   [Proses Anak (fork04)] (PID: ..., PPID: ...)
                        |                                    |
                        | (Menunggu Anak)                     | (Menjalankan Kode Anak)
                        |                                    |
                        | (Selesai setelah Anak selesai)      | (Selesai)
```
penjelasan fork04:  
Proses induk mencetak pesan dan menunggu proses anak selesai menggunakan wait(). Proses anak mencetak pesan dan kemudian keluar.
```
$ ./fork05
```
#include <iostream>
using namespace std;
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>
/* pid_t fork() dideklarasikan pada unistd.h.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/

int main(void) {
  pid_t child_pid;
  int status; 
  pid_t wait_result;
  child_pid = fork();
  if (child_pid == 0) {
    /* kode ini hanya dieksekusi proses child */
    cout << "I am a child and my pid = " << getpid() << endl;
    execl("/bin/ls", "ls", "-l", "/home", NULL);
    /* jika execl berhasil kode ini tidak pernah digunakan */
    cout << "Could not execl file /bin/ls" << endl;
    exit(1);
    /* exit menghentikan hanya proses child */
   }
  else if (child_pid > 0) {
    /* kode ini hanya mengeksekusi proses parent */
   cout << "I am the parent and my pid = " << getpid() << endl;
   cout << "My child has pid = " << child_pid << endl;
  }
  else {
   cout << "The fork system call failed to create a new process" << endl;
   exit(1);
  }
  /* kode ini hanya dieksekusi oleh proses parent karena
  child mengeksekusi dari “/bin/ls” atau keluar */
   cout << "I am a happy, healthy process and my pid = " << getpid() << endl;
   if (child_pid == 0) {
  /* kode ini tidak pernah dieksekusi */
   printf("This code will never be executed!\n");
  }
  else {
   /* kode ini hanya dieksekusi oleh proses parent */
    cout << "I am a parent and I am going to wait for my child" << endl;
    do {
      /* parent menunggu sinyal SIGCHLD mengirim tanda bila proses child diterminasi */
      wait_result = wait(&status);
    } while (wait_result != child_pid);
    cout << "I am a parent and I am quitting." << endl;
  }
  return 0;
}
```
![fork5](https://github.com/Naurilputri/SisOpe-2025/blob/main/screenshots_fork/fork05.png)  
```
                                  [Proses Utama (fork05)] (PID: ..., PPID: ...)
                                          |
                                          | fork()
                                          |
                        --------------------------------------
                        |                                    |
            [Proses Induk (fork05)] (PID: ..., PPID: ...)   [Proses Anak (ls -l /home)] (PID: ..., PPID: ...)
                        |                                    |
                        | (Menunggu Anak)                     | (Menjalankan ls -l /home)
                        |                                    |
                        | (Selesai setelah Anak selesai)      | (Selesai)
```
penjelasan fork05:  
Proses anak menjalankan perintah ls -l /home menggunakan execl(). Output dari perintah ls -l /home (yaitu, daftar file dan direktori di dalam direktori /home) ditampilkan. Setelah proses anak selesai, proses induk keluar (wait()).
```
$ ./fork06
```
#include <iostream>
using namespace std;
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>
/* pid_t fork() dideklarasikan pada unistd.h.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/

int main(void) {
	pid_t child_pid;
	int status;
	pid_t wait_result;
	child_pid = fork();


	if (child_pid == 0) {
		/* kode ini hanya dieksekusi proses child */
		cout << "I am a child and my pid = " << getpid() << endl;
		execl("fork03", "goose", NULL);
		/* jika execl berhasil kode ini tidak pernah digunakan */
		cout << "Could not execl file fork3" << endl;
		exit(1);
		/* exit menghentikan hanya proses child */
	}
	else if (child_pid > 0) {
		/* kode ini hanya mengeksekusi proses parent */
		cout << "I am the parent and my pid = " << getpid()<< endl;
		cout << "My child has pid = " << child_pid << endl;
	}
	else {
		cout << "The fork system call failed to create a new process" << endl;
		exit(1);
	}
	/* kode ini hanya dieksekusi oleh proses parent karena
	child mengeksekusi dari “fork3” atau keluar */
		cout << "I am a happy, healthy process and my pid = " << getpid() << endl;
		if (child_pid == 0) {
	/* kode ini tidak pernah dieksekusi */
		printf("This code will never be executed!\n");
	}
	else {
	/* kode ini hanya dieksekusi oleh proses parent */
		cout << "I am a parent and I am going to wait for my child" << endl;
		do {
		/* parent menunggu sinyal SIGCHLD mengirim tanda
		bila proses child diterminasi */
			wait_result = wait(&status);
		} while (wait_result != child_pid);
		cout << "I am a parent and I am quitting." << endl;
	}
	return 0;
}
```
![fork6](https://github.com/Naurilputri/SisOpe-2025/blob/main/screenshots_fork/fork06.png)  
```
                                  [Proses Utama (fork06)] (PID: ..., PPID: ...)
                                          |
                                          | fork()
                                          |
                        --------------------------------------
                        |                                    |
            [Proses Induk (fork06)] (PID: ..., PPID: ...)   [Proses Anak (fork03)] (PID: ..., PPID: ...)
                        |                                    |
                        | (Menunggu Anak)                     | (Menjalankan fork03)
                        |                                    |
                        | (Selesai setelah Anak selesai)      | (Selesai)
```
penjelasan fork06:
Fungsi execl() mengganti kode yang sedang berjalan dengan kode dari program lain (fork03). Fungsi wait() membuat proses induk menunggu hingga proses anak selesai.
