# # Multithreaded Web Crawler using Parallel Computing

## Introduction

This project implements a **Multithreaded Web Crawler** in C++ that automatically traverses web pages, downloads HTML content, and extracts hyperlinks for further exploration. The crawler follows a **Worker-Pool Architecture** where multiple threads work concurrently to improve crawling efficiency and reduce the impact of network latency.

The project was developed as part of the **Parallel and Distributed Computing (PDC)** course to demonstrate practical applications of multithreading, synchronization, shared memory, and producer-consumer design patterns.

---

## Project Description

The crawler starts from a seed URL and recursively visits pages within the same domain.

### Features

* Multi-threaded crawling using POSIX Threads (Pthreads)
* Concurrent webpage downloading using libcurl
* Automatic hyperlink extraction
* Domain-restricted crawling
* HTML page storage
* Activity logging
* Thread-safe URL queue management
* Error handling and recovery

---

## PDC Core Concepts Used

### 1. Multithreading

Multiple worker threads execute simultaneously, allowing several webpages to be downloaded and processed in parallel.

### 2. Shared Memory Model

All threads share common resources such as:

* URL Queue
* Visited URL Set
* Statistics Counters
* Log Files

This demonstrates the shared-memory architecture used in parallel computing.

### 3. Producer-Consumer Architecture

The system follows a producer-consumer model:

* Parser acts as a Producer by generating new URLs.
* Worker Threads act as Consumers by processing URLs from the queue.

### 4. Mutex Synchronization

Mutex locks protect shared resources and prevent race conditions when multiple threads access the same data.

### 5. Condition Variables

Condition variables allow threads to sleep when the queue is empty and wake up when new URLs become available, eliminating busy waiting.

### 6. Load Balancing

The shared URL queue dynamically distributes work among available threads, ensuring efficient utilization of resources.

### 7. Data Decomposition

Downloaded webpages are decomposed into smaller tasks by extracting hyperlinks, which are then redistributed to worker threads.

---

## Project Architecture

### Modules

#### URL Queue

Responsible for managing pending URLs in a thread-safe manner.

#### Crawler

Coordinates worker threads and manages page downloading.

#### Parser

Extracts hyperlinks from downloaded HTML pages.

#### Saver

Stores downloaded webpages into local files.

#### Logger

Records crawler activities and error events.

---

## Technologies Used

* C++
* POSIX Threads (Pthreads)
* libcurl
* Regular Expressions (Regex)
* Kali Linux

---

## Outputs

The crawler successfully:

* Downloads webpages concurrently.
* Extracts hyperlinks automatically.
* Stores retrieved pages as HTML files.
* Maintains detailed activity logs.
* Stops safely after reaching the specified page limit.

### Generated Outputs

* page_1.html
* page_2.html
* page_3.html
* ...
* page_23.html

### Log File

crawler.log

Contains:

* Download activities
* Thread operations
* Error messages
* Execution timestamps

---

## Error Handling

The crawler is designed to handle various failure scenarios:

| Error Scenario     | Handling Mechanism                      |
| ------------------ | --------------------------------------- |
| Network Timeout    | Logs failure and continues execution    |
| Invalid URL        | Skips invalid links safely              |
| DNS Lookup Failure | Records error without crashing          |
| Race Conditions    | Prevented using mutex locks             |
| Empty Queue        | Threads sleep using condition variables |

---

## Learning Outcomes

Through this project, the following Parallel Computing concepts were practically implemented:

* Thread Creation and Management
* Synchronization Mechanisms
* Shared Memory Programming
* Producer-Consumer Design Pattern
* Load Balancing Techniques
* Concurrent I/O Operations
* Parallel Task Scheduling

---

## Conclusion

This project successfully demonstrates how parallel computing techniques can significantly improve the performance of network-bound applications. By utilizing multiple threads, shared-memory communication, mutex synchronization, and condition variables, the crawler efficiently downloads and processes webpages while maintaining correctness and stability.

The implementation provided hands-on experience with core Parallel and Distributed Computing concepts and highlighted the importance of synchronization and resource management in concurrent systems.

---

## Course

Parallel and Distributed Computing (PDC)

## Environment

* Kali Linux
* C++
* POSIX Threads
* libcurl

