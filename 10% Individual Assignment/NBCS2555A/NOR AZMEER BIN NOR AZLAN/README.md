# Evaluating High-Concurrency Throughput and Latency of RESTful Services using Autocannon

## Student Information
* **Name:** Nor Azmeer Bin Nor Azlan 
* **Student ID:** 2024389117 
* **Group:** NBCS2555A 
* **Course:** ITT440 - Network Programming 

## Introduction
This project evaluates the performance of a RESTful service using the **Platzi Fake Store API**.
The study measures throughput, identifies server breaking points, and analyzes error handling under stress.

## Methodology
### Tools Used
* **Autocannon:** Node.js-based HTTP benchmarking tool.
* **Environment:** Node.js v24.15.0 on Windows.

### Target API
* **Endpoint:** `https://api.escuelajs.co/api/v1/products`

## Test Scenarios & Results

| Test Type | Connections | Command | Avg Latency | Avg Req/Sec | Success Rate |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Load Test** | 20 | `autocannon -c 20 -d 30` | 283.25 ms | 70.87 | 100%  |
| **Stress Test** | 100 | `autocannon -c 100 -d 30` | 249.64 ms | 400.17 | 100%  |
| **Flood Test** | 500 (p10) | `autocannon -c 500 -p 10 -d 20` | 1710.85 ms | 1,141.25 | 85%  |

## Discussion
* **Stability:** The system remained stable up to 100 concurrent connections.
* **Breaking Point:** At 500 connections with pipelining, the server exceeded resource limits, resulting in **5,000 timeout errors**.
* **Latency:** Average latency spiked from ~280ms to 1.7 seconds during the flood test.

## Conclusion
The API is suitable for standard use but requires horizontal scaling or stricter rate-limiting to handle enterprise-level spikes.
