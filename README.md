# 💻 RESTful Booker - Performance Testing Project

## 🔗 Live Demo

<a href="https://restful-booker.herokuapp.com/apidoc/index.html">👉 Click Here to View</a>

---

## 📁 What's Included

- ✅ **JMeter Test Plan** – Configures and organizes the performance testing scenarios.
- ✅ **Load Test** – Simulates 10 virtual users with a 1-second ramp-up period and 1 loop.
- ✅ **Stress Test** – Simulates 50 virtual users with a 100-second ramp-up period and 5 loops.
- ✅ **Spike Test** – Uses Ultimate Thread Group to simulate three sudden workload increases, reaching 150 concurrent virtual users during each spike.
- ✅ **Soak Test** – Simulates 10 virtual users continuously for 300 seconds (5 minutes) to evaluate system stability under sustained load.
- ✅ **CSV Test Data** – Provides authentication data where configured.
- ✅ **Performance Results** – Separate CSV/JTL results files and HTML dashboards for each test scenario.
- ✅ **README Documentation** – Explains the test scenarios, configurations, and execution steps.

---

## ✅ What's Tested

### ⚙️ Load Testing

Simulates a normal workload to evaluate API performance under expected usage conditions.

**Load Test Configuration:**

| Setting | Value |
|---|---:|
| Threads (Users) | 10 |
| Ramp-Up Period | 1 second |
| Loop Count | 1 |

**Test Objectives:**

- Simulate 10 concurrent virtual users.
- Evaluate API behavior under the configured workload.
- Measure response times and throughput.
- Monitor failed requests and error rates.

### 🔥 Stress Testing

Simulates a higher workload to evaluate API behavior under increased user activity.

**Stress Test Configuration:**

| Setting | Value |
|---|---:|
| Threads (Users) | 50 |
| Ramp-Up Period | 100 seconds |
| Loop Count | 5 |

**Test Objectives:**

- Simulate 50 virtual users.
- Evaluate API behavior under a higher workload.
- Monitor response times as the workload increases.
- Identify performance degradation and potential bottlenecks.
- Analyze throughput and error rates.

### ⚡ Spike Testing

Uses **Ultimate Thread Group** to simulate three sudden increases in workload and evaluate how the API responds to rapid changes in concurrent users.

**Spike Test Configuration:**

| Row / Phase | Start Threads Count | Initial Delay | Startup Time | Hold Load For | Shutdown Time |
|---|---:|---:|---:|---:|---:|
| Baseline | 10 | 0s | 5s | 300s | 5s |
| Spike 1 | 30 | 40s | 3s | 30s | 5s |
| Spike 2 | 75 | 120s | 3s | 30s | 5s |
| Spike 3 | 150 | 200s | 5s | 30s | 5s |

*All time values are in seconds.*

**Expected Execution:**

1. **Baseline:** Start with 10 virtual users.
2. **First Spike:** Add 30 users after 40 seconds, reaching approximately 40 concurrent users.
3. **Recovery:** The additional 30 users finish their scheduled period, returning the workload to the 10-user baseline.
4. **Second Spike:** Add another 75 users after 120 seconds, reaching approximately 85 concurrent users.
5. **Recovery:** Return to the 10-user baseline.
6. **Third Spike:** Add another 150 users after 200 seconds, reaching approximately 160 concurrent users.
7. **Final Recovery:** The additional users finish, leaving the baseline workload.
8. **Completion:** The baseline Thread Group finishes its scheduled execution.

**Test Objectives:**

- Evaluate API behavior during sudden increases in concurrent users.
- Monitor response times during each spike.
- Identify performance bottlenecks under sudden workload changes.
- Observe recovery behavior after each spike.
- Analyze error rates and throughput during peak workloads.

### ♨️ Soak Testing

Uses a standard **Thread Group** to maintain a sustained workload over an extended period and evaluate API stability.

**Soak Test Configuration:**

| Setting | Value |
|---|---:|
| Threads (Users) | 10 |
| Ramp-Up Period | 10 seconds |
| Loop Count | Forever |
| Specify Thread Lifetime | Enabled |
| Duration | 300 seconds (5 minutes) |
| Startup Delay | 0 seconds |

**Test Objectives:**

- Maintain 10 virtual users over a continuous 5-minute period.
- Monitor API response times and throughput over time.
- Identify potential performance degradation.
- Detect increasing error rates during sustained execution.
- Evaluate API stability under continuous workload.

**Execution:** The Soak Test runs for 300 seconds with 10 virtual users and an infinite loop count, subject to the configured thread lifetime.

---

## 🌐 API Endpoints Tested

The following RESTful Booker API endpoints are included in the test scenarios:

| API Functionality | HTTP Method | Endpoint |
|---|---|---|
| Authentication | POST | `/auth` |
| Get Booking IDs | GET | `/booking` |
| Get Booking by ID | GET | `/booking/58` |
| Create Booking | POST | `/booking` |

---

## 📄 How to Run the Tests

### Step 1: Install Apache JMeter

Download and install Apache JMeter from the official website:

[Apache JMeter Download](https://jmeter.apache.org/download_jmeter.cgi)

Make sure Java is installed and configured correctly.

### Step 2: Install JMeter Plugins

The Spike Test uses **Ultimate Thread Group**, which is provided by JMeter Plugins.

1. Download and install [JMeter Plugins Manager](https://jmeter-plugins.org/wiki/PluginsManager/).
2. Open Apache JMeter.
3. Navigate to **Options → Plugins Manager**.
4. Find and install **Custom Thread Groups**.
5. Restart JMeter.

### Step 3: Open the Test Plan

1. Launch Apache JMeter.
2. Open `Test_Plan.jmx`.
3. Review the Thread Groups and HTTP Request Defaults.
4. Verify the API base URL and request configurations.

### Step 4: Configure Test Data

The test plan uses `Users Account.csv` for authentication data, where configured.

1. Place the CSV file in the project directory.
2. Open the CSV Data Set Config element.
3. Verify the filename, variable names, delimiter, and credentials.
4. If the file path contains a location specific to your computer, update it to a valid path.

For example, if the CSV file is in the same directory as the JMX file, use:

```text
Users Account.csv
```

### Step 5: Run the Load Test

1. Enable the **Load Test** Thread Group.
2. Disable all other Thread Groups.
3. Verify the configuration:
   - Threads (Users): `10`
   - Ramp-Up Period: `1` second
   - Loop Count: `1`
4. Run the test.
5. Review the results.

### Step 6: Run the Stress Test

1. Enable the **Stress Test** Thread Group.
2. Disable all other Thread Groups.
3. Verify the configuration:
   - Threads (Users): `50`
   - Ramp-Up Period: `100` seconds
   - Loop Count: `5`
4. Run the test separately.
5. Review the results.

### Step 7: Run the Spike Test

1. Enable the **Spike Test** Ultimate Thread Group.
2. Disable all other Thread Groups.
3. Verify the four schedule rows in the Ultimate Thread Group configuration.
4. Confirm the three spike periods:
   - First Spike: `40` seconds.
   - Second Spike: `120` seconds.
   - Third Spike: `200` seconds.
5. Verify the startup, hold, and shutdown times.
6. Run the test separately.
7. Review the results during each spike and recovery period.

### Step 8: Run the Soak Test

1. Enable the **Soak Test** Thread Group.
2. Disable all other Thread Groups.
3. Verify the configuration:
   - Threads (Users): `10`
   - Ramp-Up Period: `10` seconds
   - Loop Count: `Forever`
   - Specify Thread Lifetime: Enabled
   - Duration: `300` seconds
   - Startup Delay: `0` seconds
4. Run the test separately.
5. Review response times, throughput, error rates, and performance stability throughout the execution.

---

## 📊 Performance Metrics

Review the following metrics after each test execution:

- ⏱️ **Response Time** – Time taken for requests to receive responses.
- 📈 **Throughput** – Number of requests processed per unit of time.
- ❌ **Error Rate** – Percentage of failed requests.
- 📊 **Average Response Time** – Average duration of recorded requests.
- 📉 **P95 Response Time** – Response-time threshold below which 95% of recorded samples fall.
- 🔢 **Total Samples** – Total number of recorded requests.

---

## 📝 Save Results and Generate HTML Dashboards

### General JMeter Command Syntax

Use the following command structure to execute a test plan, save its results, and generate an HTML dashboard automatically:

```cmd
jmeter -n -t [Path Folder\Test_Plan.jmx] -l [Path Folder\Results File.csv] -e -o [Path Folder\HTML Report Folder]
```

**Command Options:**

- `-n` – Run JMeter in non-GUI mode.
- `-t` – Specify the JMX test plan file.
- `-l` – Specify the output file for test results.
- `-e` – Generate the HTML dashboard after the test finishes.
- `-o` – Specify the output directory for the HTML dashboard.

### Step 1: Run the Load Test and Generate an HTML Dashboard

```cmd
jmeter -n -t [Path Folder\Test_Plan.jmx] -l [Path Folder\load_test_worklogs.csv] -e -o [Path Folder\HTML_Performance_Load_Test_Report]
```

### Step 2: Run the Stress Test and Generate an HTML Dashboard

```cmd
jmeter -n -t [Path Folder\Test_Plan.jmx] -l [Path Folder\stress_test_worklogs.csv] -e -o [Path Folder\HTML_Performance_Stress_Test_Report]
```

### Step 3: Run the Spike Test and Generate an HTML Dashboard

```cmd
jmeter -n -t [Path Folder\Test_Plan.jmx] -l [Path Folder\spike_test_worklogs.csv] -e -o [Path Folder\HTML_Performance_Spike_Test_Report]
```

### Step 4: Run the Soak Test and Generate an HTML Dashboard

```cmd
jmeter -n -t [Path Folder\Test_Plan.jmx] -l [Path Folder\soak_test_worklogs.csv] -e -o [Path Folder\HTML_Performance_Soak_Test_Report]
```

### 📝 Run JMeter Test in Non-GUI Mode

You can also execute a test without generating an HTML dashboard:

```cmd
jmeter -n -t [your_test_plan.jmx] -l [your_output_file.jtl]
```

**Important Notes:**

- All commands use the same `Test_Plan.jmx` file.
- Enable only the intended Thread Group before each execution and disable all other scenarios.
- JMeter executes the enabled Thread Groups saved in the JMX file. Make sure the correct scenario is enabled before running each command.
- Ensure each HTML report output directory is empty or does not already exist.
- Use a separate results file and HTML report directory for every scenario.
- Disable **View Results Tree** and other unnecessary listeners during non-GUI performance executions to reduce resource consumption.
- Keep the JMeter client machine's CPU and memory usage under observation, especially during Spike and Soak Testing.

---

## 🧰 Tools Used

- **Apache JMeter** – Performance testing and workload simulation.
- **JMeter Plugins Manager** – Installing additional Thread Group components.
- **Ultimate Thread Group** – Configuring multiple workload stages and sudden load increases.
- **RESTful Booker API** – API under test.
- **CSV Test Data** – External test data, including authentication data where configured.
- **CSV Results Files** – Storage of recorded JMeter test results.
- **HTML Dashboard Reports** – Visualization and analysis of performance test results.

---
