# LAPORAN TUGAS
## MATAKULIAH SISTEM OPERASI
### SISTEM FILE DAN THREAD

Dosen Pengampu:

**Dr. Ferry Astika Saputra ST, M.Sc**

Disusun Oleh:

**Nauril Putri Hadining Tyas (3124521012)**

**PROGRAM STUDI D3 TEKNIK INFORMATIKA PSDKU LAMONGAN**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**


## a. Penerapan Thread pada SumTask.java

```java
/**
 * Fork/join parallelism in Java
 *
 * Figure 4.18
 *
 * @author Gagne, Galvin, Silberschatz
 * Operating System Concepts  - Tenth Edition
 * Copyright John Wiley & Sons - 2018
 */

import java.util.concurrent.*;

public class SumTask extends RecursiveTask<Integer>
{
    static final int SIZE = 10000;
    static final int THRESHOLD = 1000;

    private int begin;
    private int end;
    private int[] array;

    public SumTask(int begin, int end, int[] array) {
        this.begin = begin;
        this.end = end;
        this.array = array;
    }

    protected Integer compute() {
        if (end - begin < THRESHOLD) {
            // conquer stage 
            int sum = 0;
            for (int i = begin; i <= end; i++)
                sum += array[i];

            return sum;
        }
        else {
            // divide stage 
            int mid = begin + (end - begin) / 2;
            
            SumTask leftTask = new SumTask(begin, mid, array);
            SumTask rightTask = new SumTask(mid + 1, end, array);

            leftTask.fork();
            rightTask.fork();

            return rightTask.join() + leftTask.join();
        }
    }

    public static void main(String[] args) {
        ForkJoinPool pool = new ForkJoinPool();
        int[] array = new int[SIZE];

        // create SIZE random integers between 0 and 9
        java.util.Random rand = new java.util.Random();

        for (int i = 0; i < SIZE; i++) {
            array[i] = rand.nextInt(10);
        }        
        
        // use fork-join parallelism to sum the array
        SumTask task = new SumTask(0, SIZE-1, array);

        int sum = pool.invoke(task);

        System.out.println("The sum is " + sum);
    }
}
```

**Tujuan Program:**  
Program `SumTask.java` bertujuan menghitung jumlah seluruh elemen array besar secara paralel menggunakan konsep *fork/join parallelism* di Java. Dengan membagi array menjadi bagian-bagian kecil dan menjalankannya secara paralel, proses perhitungan menjadi lebih cepat dan efisien.

**Cara Membuat dan Menjalankan Thread:**  
Program menggunakan `ForkJoinPool` untuk mengelola beberapa thread. Kelas `SumTask` memperluas `RecursiveTask<Integer>` dan mengimplementasikan metode `compute()`. Jika ukuran array lebih kecil dari `THRESHOLD`, array dijumlahkan secara langsung. Jika tidak, array dibagi menjadi dua sub-tugas menggunakan `fork()`, dan hasil keduanya digabungkan dengan `join()`.

**Interaksi antar Thread:**  
Setiap sub-tugas dipanggil menggunakan `fork()`, lalu hasilnya dikumpulkan menggunakan `join()`. `fork()` membuat thread baru untuk mengerjakan sub-tugas, dan `join()` menunggu hingga sub-tugas tersebut selesai.

**Perbedaan Java vs Linux vs Windows:**  
Java menyediakan API tingkat tinggi melalui JVM yang mempermudah pengelolaan thread. Berbeda dengan Linux (pthreads) dan Windows (CreateThread) yang membutuhkan manajemen manual terhadap thread.

---

## b. Penerapan Thread di Linux (thrd-posix.c)

```c
/**
 * A pthread program illustrating how to
 * create a simple thread and some of the pthread API
 * This program implements the summation function where
 * the summation operation is run as a separate thread.
 *
 * Most Unix/Linux/OS X users
 * gcc thrd.c -lpthread
 *
 * Figure 4.11
 *
 * @author Gagne, Galvin, Silberschatz
 * Operating System Concepts  - Tenth Edition
 * Copyright John Wiley & Sons - 2018
 */

#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>

int sum; /* this data is shared by the thread(s) */

void *runner(void *param); /* the thread */

int main(int argc, char *argv[])
{
    pthread_t tid; /* the thread identifier */
    pthread_attr_t attr; /* set of attributes for the thread */

    if (argc != 2) {
        fprintf(stderr,"usage: a.out <integer value>
");
        return -1;
    }

    if (atoi(argv[1]) < 0) {
        fprintf(stderr,"Argument %d must be non-negative
",atoi(argv[1]));
        return -1;
    }

    /* get the default attributes */
    pthread_attr_init(&attr);

    /* create the thread */
    pthread_create(&tid, &attr, runner, argv[1]);

    /* now wait for the thread to exit */
    pthread_join(tid, NULL);

    printf("sum = %d
", sum);
}

/**
 * The thread will begin control in this function
 */
void *runner(void *param) 
{
    int i, upper = atoi(param);
    sum = 0;

    if (upper > 0) {
        for (i = 1; i <= upper; i++)
            sum += i;
    }

    pthread_exit(0);
}
```

**Tujuan Program:**  
Program `thrd-posix.c` menunjukkan bagaimana membuat dan mengelola thread menggunakan POSIX Threads (`pthread`) di sistem operasi Linux.

**Cara Membuat dan Menjalankan Thread:**  
Thread dibuat menggunakan `pthread_create()`, yang menerima fungsi `runner` sebagai tugas yang dijalankan. Setelah membuat thread, `pthread_join()` digunakan untuk menunggu hingga thread selesai sebelum melanjutkan eksekusi program utama.

**Interaksi antar Thread:**  
`pthread_create()` membuat thread baru, lalu `pthread_join()` dipanggil untuk menunggu thread tersebut selesai, memastikan sinkronisasi antar-thread.

---

## c. Penerapan Thread di Windows (thrd-win32.c)

```c
/**
 * This program creates a separate thread using the CreateThread() system call.
 *
 * Figure 4.13
 *
 * @author Gagne, Galvin, Silberschatz
 * Operating System Concepts  - Tenth Edition
 * Copyright John Wiley & Sons - 2018
 */

#include <stdio.h>
#include <windows.h>

DWORD Sum; /* data is shared by the thread(s) */

/* the thread runs in this separate function */
DWORD WINAPI Summation(PVOID Param)
{
    DWORD Upper = *(DWORD *)Param;
    for (DWORD i = 0; i <= Upper; i++)
        Sum += i;
    return 0;
}

int main(int argc, char *argv[])
{
    DWORD ThreadId;
    HANDLE ThreadHandle;
    int Param;

    // do some basic error checking
    if (argc != 2) {
        fprintf(stderr,"An integer parameter is required
");
        return -1;
    }

    Param = atoi(argv[1]);
    if (Param < 0) {
        fprintf(stderr, "an integer >= 0 is required 
");
        return -1;
    }

    // create the thread
    ThreadHandle = CreateThread(NULL, 0, Summation, &Param, 0, &ThreadId);

    if (ThreadHandle != NULL) {
        WaitForSingleObject(ThreadHandle, INFINITE);
        CloseHandle(ThreadHandle);
        printf("sum = %d
", Sum);
    }
}
```

**Tujuan Program:**  
Program `thrd-win32.c` memperlihatkan pembuatan dan sinkronisasi thread menggunakan API Windows (`CreateThread`).

**Cara Membuat dan Menjalankan Thread:**  
Thread dibuat dengan `CreateThread()`, lalu `WaitForSingleObject()` digunakan untuk menunggu hingga thread selesai.

**Interaksi antar Thread:**  
`CreateThread()` menciptakan thread baru, dan `WaitForSingleObject()` membuat thread utama menunggu hingga thread baru selesai.

---

## KESIMPULAN

Praktikum ini mengajarkan bagaimana thread dikelola di Java, Linux, dan Windows. Java menawarkan kemudahan dengan API tingkat tinggi, sedangkan Linux dan Windows menawarkan fleksibilitas lebih besar namun memerlukan manajemen lebih rinci. Pemahaman ini penting untuk pengembangan perangkat lunak berbasis multithreading yang optimal dan aman.
