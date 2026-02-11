# SOFE4630U-Milestone3-Dataflow

## Project Overview
This milestone demonstrates the implementation of scalable batch and streaming data processing pipelines using Google Cloud Dataflow and Apache Beam.

The main objectives of this project were to:
- Understand and apply the MapReduce programming model
- Build scalable batch pipelines
- Build real-time streaming pipelines
- Integrate Dataflow with BigQuery, Pub/Sub, Cloud Storage, and TensorFlow
- Design a custom smart meter data preprocessing pipeline

The milestone showcases how Dataflow can serve as a unified platform for distributed analytics and machine learning inference.

---

## Technologies Used
- Google Cloud Platform (GCP)
- Google Cloud Dataflow
- Apache Beam (Python SDK)
- Google Cloud Storage
- Google BigQuery
- Google Pub/Sub
- TensorFlow (Pre-trained MNIST model)
- Python 3.x

---

## Repository Structure
- wordcount/                  # Basic WordCount pipeline
- wordcount2/                 # Enhanced WordCount with branching
- mnist/                      # MNIST batch and streaming pipelines
  - mnistBQ.py
  - mnistPubSub.py
  - setup.py
- design/
  - smartmeterDataflow.py     # Smart meter preprocessing pipeline
- README.md

---

## Dataflow Examples

### 1. WordCount Pipeline (Batch)
This pipeline demonstrates a basic MapReduce implementation using Apache Beam.

- Reads Shakespeare text from Cloud Storage
- Splits lines into words (Map)
- Converts words into key-value pairs (word, 1)
- Groups by key and sums counts (Reduce)
- Writes results to Cloud Storage

Concepts demonstrated:
- Map
- Reduce
- GroupByKey
- Distributed execution using DataflowRunner

---

### 2. Enhanced WordCount with Branching
This example extends the basic WordCount by introducing parallel branching.

Pipeline structure:
- Preprocesses words (lowercase conversion)
- Splits into two parallel branches

Branch 1:
- Filters words starting with letters a–f
- Performs word count

Branch 2:
- Extracts first letter of each word
- Counts frequency of each letter

Demonstrates:
- Parallel pipeline branching
- Multiple outputs from a single input stream
- Advanced Apache Beam transformations

---

### 3. MNIST Batch Processing (BigQuery + TensorFlow)
This pipeline performs large-scale machine learning inference.

- MNIST dataset uploaded to BigQuery
- Dataflow reads image records
- TensorFlow model performs digit classification
- Prediction probabilities (P0–P9) written back to BigQuery

Key concepts:
- BigQuery integration
- Singleton model loading per worker
- Scalable distributed ML inference
- Automatic table creation and overwrite

---

### 4. MNIST Streaming Processing (Pub/Sub)
This example demonstrates real-time digit classification.

Workflow:
- MNIST image records published to Pub/Sub topic
- Streaming Dataflow pipeline consumes messages
- TensorFlow model performs inference
- Predictions published to output topic
- Consumer retrieves predictions in real time

Demonstrated concepts:
- Streaming pipelines
- Pub/Sub integration
- Low-latency ML inference
- Continuous execution

---

### 5. Design: Smart Meter Data Preprocessing Pipeline
A custom streaming pipeline designed for preprocessing smart meter measurements.

Pipeline steps:
1. Read from Pub/Sub (meter_raw topic)
2. Filter invalid records (remove messages with None values)
3. Convert units:
   - Pressure: P(psi) = P(kPa) / 6.895
   - Temperature: T(F) = T(C) * 1.8 + 32
4. Write cleaned data to Pub/Sub (meter_clean topic)

Demonstrates:
- Real-time validation
- Data transformation
- IoT-style streaming preprocessing
- Pub/Sub-to-Pub/Sub architecture

---

## Results
All pipelines executed successfully in both batch and streaming modes.

The project demonstrates:
- Scalable MapReduce execution
- Cloud-native integration
- Distributed machine learning inference
- Real-time streaming analytics
- Fault-tolerant data processing

---

## Deliverables
- Final Report (PDF)
- Video 1 – WordCount & MNIST Examples
- Video 2 – Smart Meter Design Pipeline

---

## Conclusion
This project demonstrates how Google Cloud Dataflow can serve as a scalable, fault-tolerant, and fully managed data processing platform capable of handling:

- Batch analytics
- Streaming analytics
- Machine learning inference
- Real-time data preprocessing

The integration of Dataflow with BigQuery, Pub/Sub, Cloud Storage, and TensorFlow highlights its suitability for modern cloud-based distributed systems.
