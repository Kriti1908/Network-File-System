
# Distributed Client-Server System

This project implements a distributed file management system that ensures high availability, fault tolerance, and efficient data management across multiple servers. The system uses hashmaps for fast data searching and incorporates backup mechanisms to safeguard data in case of server failure. It also allows servers to synchronize and recover data when they come back online after being offline.

## Features

1. **Efficient Data Search with Hashmaps**  
   - Hashmaps are used for fast lookups, ensuring that client requests can be processed efficiently even with large datasets.
   - Each server maintains a hashmap of data for quick access based on unique keys.

2. **Multi-Client and Multi-Server Support**  
   - The system supports multiple servers, each managing different subsets of data.
   - Multiple clients can interact with the servers concurrently, allowing for load balancing and better resource utilization.

3. **Data Backup Mechanism**  
   - Each server maintains a backup of its data to ensure data safety even in the event of server failure.
   - Backup copies are kept locally and synchronized regularly to prevent data loss.

4. **Seamless Server Recovery**  
   - In case a server goes offline, the data is backed up across other servers.
   - When a server comes back online after being offline for a period, it automatically syncs with the backup data from other servers to restore its data.
   - This ensures no data is lost and the system remains consistent even with intermittent server outages.

5. **Fault Tolerance and High Availability**
   - The system is designed to be fault-tolerant and highly available. Multiple replicas of data are maintained across different servers, so if one server fails, another server can continue to serve client requests with minimal disruption.
   - Automatic backup and recovery mechanisms ensure seamless operation even during server failures.

## Architecture Overview

1. **Client-Server Communication**:  
   - Communication is implemented using efficient socket programming, supporting both request-response and event-driven paradigms.  

2. **Backup System**:  
   - Servers use a periodic backup mechanism to ensure data consistency across the distributed system.  

3. **Fault Tolerance**:  
   - The system detects server failures and re-routes client requests to available servers. Upon recovery, servers reconcile any data differences using synchronization logic.

4. **Data Structures**:  
   - Hashmaps play a key role in fast lookup operations for server data, ensuring minimal latency during searches.

## How It Works

1. **Initialization**:  
   - Start the servers, which register themselves with a central monitoring service.  
   - Clients can connect to any available server.  

2. **Request Handling**:  
   - Clients send requests to servers, which process and respond using a shared protocol.  

3. **Backup Management**:  
   - Each server periodically backs up its data locally and to designated backup servers.  

4. **Failure and Recovery**:  
   - If a server goes offline, its data remains in the backup.  
   - When the server comes back online, it updates its dataset using backup data and synchronizes with other servers.

## Installation

1. Clone the repository:  
   ```bash
   git clone https://github.com/yourusername/Network-File-System.git
   cd Network-File-System
   ```

2. Run the Makefile:  
   ```bash
   make
   ```

3. Run the naming server:  
   ```bash
   ./n
   ```

4. Run the storage servers:  
   ```bash
   ./s 
   ```

5. Run the clients:
   ```bash
   ./c
   ```