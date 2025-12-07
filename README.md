# Memory Leak Demonstration in C (Azure VM Experiment)

This project demonstrates how a simple C program can create a memory leak by repeatedly allocating 50MB blocks of memory without freeing them. Running this on a 16GB Azure VM shows how RAM fills, virtual memory becomes exhausted, and system performance degrades as swap usage increases. :contentReference[oaicite:0]{index=0}

---

## 📌 Overview

Memory leaks in C occur when allocated memory is never released. This experiment intentionally creates a leak to observe:

- Increasing RAM consumption  
- Virtual memory exhaustion  
- System slowdown due to swap usage  
- Differences between unmanaged C memory and garbage-collected runtimes (.NET / JVM)

---

## 🧪 Code Sample

```c
size_t size = 1024 * 1024 * 50; // 50MB

while (1) {
    void* p = malloc(size);
    if (!p) {
        printf("Allocation failed.\n");
        break;
    }
}
