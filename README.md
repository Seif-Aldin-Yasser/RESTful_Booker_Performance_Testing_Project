# 💻 RESTful Booker - API Performance Testing Project

## 🔗 Live Demo

<a href="https://restful-booker.herokuapp.com/apidoc/index.html">👉 Click Here to View</a>

---

## 📁 What's Included

* ✅ **JMeter Test Plan** – Configures and organizes the performance tests.
* ✅ **Load Test** – Simulates 10 virtual users with a 1-second ramp-up period and 1 loop count.
* ✅ **Stress Test** – Simulates 50 virtual users with a 100-second ramp-up period and 5 loop count.
* ✅ **CSV Test Data** – Provides authentication data where configured.
* ✅ **Performance Results** – Results generated from the separate Load Test and Stress Test executions.
* ✅ **README Documentation** – Explains the test scenarios, configuration, and execution steps.

---

## ✅ What's Tested

### ⚙️ Load Testing

* Configure 10 virtual users.
* Set the ramp-up period to 1 second.
* Execute 1 loop count.
* Observe API behavior under the configured workload.
* Review response times, throughput, and error rates.

### ⚙️ Stress Testing

* Configure 50 virtual users.
* Set the ramp-up period to 100 seconds.
* Execute 5 loops count.
* Observe API behavior under a higher configured workload.
* Review response times, throughput, and error rates.

**Execution:** The Load Test and Stress Test were each executed once, in separate runs.

### 🌐 API Endpoints Tested

* 🔐 **Authentication** – `POST /auth`
* 🎫 **Get Booking IDs** – `GET /booking`
* 🧾 **Get Booking by ID** – `GET /booking/12`
* ➕ **Create Booking** – `POST /booking`

---

## 📄 How to Run the Tests

### Step 1: Install Apache JMeter

Download and install Apache JMeter from the official website:

https://jmeter.apache.org/download_jmeter.cgi

Make sure Java is installed and configured correctly.

### Step 2: Open the Test Plan

1. Launch Apache JMeter.
2. Open `Test_Plan.jmx`.
3. Review the Thread Groups and HTTP Request Defaults.
4. Verify the API base URL and request configurations.

### Step 3: Configure Test Data

The test plan uses `Users Account.csv` for authentication data, where configured.

1. Place the CSV file in the project directory.
2. Open the CSV Data Set Config element.
3. Verify the filename, variable names, delimiter, and credentials.
4. If the file path contains a location specific to your computer, update it to a valid path.

For example, if the CSV file is in the same directory as the JMX file, use:

`Users Account.csv`

### Step 4: Run the Load Test

1. Enable the **Load Test** Thread Group.
2. Disable the **Stress Test** Thread Group.
3. Verify the configuration:

   * Threads (Users): `10`
   * Ramp-Up Period: `1` second
   * Loop Count: `1`
4. Run the test.
5. Review the results.

### Step 5: Run the Stress Test

1. Enable the **Stress Test** Thread Group.
2. Disable the **Load Test** Thread Group.
3. Verify the configuration:

   * Threads (Users): `50`
   * Ramp-Up Period: `100` seconds
   * Loop Count: `5`
4. Run the test separately.
5. Review the results.

   
---

## 📊 Performance Metrics

Review the following metrics after each execution:

* ⏱️ **Response Time** – Time taken for requests to receive responses.
* 📈 **Throughput** – Number of requests processed per unit of time.
* ❌ **Error Rate** – Percentage of failed requests.
* 📊 **Average Response Time** – Average duration of recorded requests.
* 📉 **P95 Response Time** – Response-time threshold for 95% of recorded samples.
* 🔢 **Total Samples** – Total number of recorded requests.


---


## 📝 Save Results and Generate HTML Dashboards

### General JMeter Command Syntax

Use the following command structure to execute a test plan, save its results, and generate an HTML dashboard automatically:

```cmd
jmeter -n -t [Path Folder\JMX File] -l [Path Folder\Results File] -e -o [Path Folder\HTML Report Folder]
```

- `-n` – Run JMeter in non-GUI mode.
- `-t` – Specify the JMX test plan file.
- `-l` – Specify the output file for test results.
- `-e` – Generate the HTML dashboard after the test finishes.
- `-o` – Specify the output directory for the HTML dashboard.


### Step 1: Run the Load Test and Generate an HTML Dashboard

Execute the following command to run the load test, save the results to a separate CSV file, and generate an HTML dashboard for analyzing load test performance:

```cmd
jmeter -n -t [Path Folder\Test_Plan.jmx] -l [Path Folder\load_test_worklogs.csv] -e -o [Path Folder\HTML_Performance_Load_Test_Report]
```

### Step 2: Run the Stress Test and Generate an HTML Dashboard

Execute the following command to run the stress test, save the results to a separate CSV file, and generate an HTML dashboard for analyzing system behavior under increasing workloads:

```cmd
jmeter -n -t [Path Folder\Test_Plan.jmx] -l [Path Folder\stress_test_worklogs.csv] -e -o [Path Folder\HTML_Performance_Stress_Test_Report]
```

**Note:** All two commands use the same `Test_Plan.jmx` file. To generate separate load and stress test reports, ensure the test plan is configured to execute only the intended test scenario for each command, or use separate JMX files for the load and stress tests.

### 🧰 Tools Used

- **Apache JMeter** – Performance testing and workload simulation.
- **RESTful Booker API** – API under test.
- **CSV Test Data** – External test data, including authentication data where configured.
- **CSV Results Files** – Storage of recorded JMeter test results.
- **HTML Dashboard Reports** – Visualization and analysis of performance test results.

---
