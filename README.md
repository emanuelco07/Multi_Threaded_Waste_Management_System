# Multi-threaded Waste Management System

A concurrent C++ simulation that models an urban waste collection system. The project demonstrates advanced multi-threading concepts, including thread synchronization, resource management, and inter-process communication using the POSIX threads (pthreads) library.

### Application Description
The application simulates a fleet of N garbage trucks. Each truck operates as an independent thread and navigates through a series of stages: departing from a garage, collecting waste in a city, crossing a restricted 2-lane bridge, unloading at specific ramps, and returning to the garage. A central supervisor thread gathers real-time data from all entities to monitor the entire system's state.

### Technologies Used
*   **Language:** C++
*   **Library:** POSIX Threads (pthreads)
*   **Synchronization Primitives:**
    *   **Semaphores:** Used for managing the 2-lane bridge capacity and access to unloading ramps.
    *   **Mutexes:** Used to protect shared variables such as truck states and the message queue.
    *   **Condition Variables:** Implemented to facilitate the producer-consumer pattern between system entities and the supervisor thread.
*   **Platform:** Linux / Unix-like environments.

### Project Requirements
*   **Independent Entities:** Every truck must be a standalone thread (th1..thN).
*   **Centralized Control:** 
    *   **Garage Thread (thgj):** Tracks all trucks and manages their deployment.
    *   **Service Thread (thrp):** Identifies faulty trucks and performs repairs before they can return to service.
    *   **Supervisor Thread (thsv):** Acts as a central logger, receiving event details from trucks, the garage, service, and ramps.
*   **Resource Constraints:** 
    *   One-lane road from the garage to the city.
    *   Two-lane bridge leading to the unloading ramps.
    *   Two dedicated unloading ramps (thrmp1, thrmp2) with integrated weighing scales.
*   **Communication:** All components must communicate using thread-safe mechanisms (Message Queues).

### Implementation Details
*   **State Machine:** Trucks transition through various states (In Garage, In City, At Semaphore, On Bridge, etc.), ensuring logical flow and data consistency.
*   **Randomized Simulation:** Realistic behavior is achieved through randomized delays for city collection times, speeds, and potential mechanical failures.
*   **Thread Safety:** Careful use of mutexes prevents race conditions when updating truck statuses or calculating total tonnage at the ramps.
*   **Graceful Shutdown:** The system monitors all trucks and ensures every thread is joined and resources are released once all scheduled tours are completed.

**Next Steps:**
*   You can place this text in your `README.md` file.
*   If you have screenshots of the terminal output (Supervisor log), you can add them using the `<table>` method we discussed earlier.

Ready for the next project! Whenever you are prepared, just send me the code and documentation.
