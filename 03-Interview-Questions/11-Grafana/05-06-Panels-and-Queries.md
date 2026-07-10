# Panels & Queries Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is a panel in Grafana?

**Answer**

A panel is an individual visualization component within a Grafana dashboard. Each panel executes a query against a configured data source and displays the returned data using a selected visualization type.

**Explanation**

A dashboard consists of one or more panels, and each panel can display different metrics or logs independently.

**Where it is used in Production**

- CPU monitoring
- Memory monitoring
- Application response time
- Request rate monitoring
- Error tracking

**Common Mistake**

Many candidates confuse a dashboard with a panel. A dashboard contains multiple panels.

---

### Question 2

**Question**

What is the Time Series panel, and when would you use it?

**Answer**

The Time Series panel displays metric values over time using line or area graphs. It is the most commonly used visualization in Grafana.

**Explanation**

Since monitoring data is time-series data, this panel helps identify trends, spikes, and performance changes over time.

**Where it is used in Production**

- CPU utilization
- Memory usage
- Network traffic
- HTTP request rate
- Application latency

---

### Question 3

**Question**

What is a Stat panel?

**Answer**

A Stat panel displays a single important value, such as the latest metric, average, minimum, or maximum value.

**Explanation**

It provides a quick summary of a metric without displaying historical trends.

**Where it is used in Production**

- Current CPU usage
- Active users
- Total requests
- Server uptime
- Available disk space

**Common Mistake**

Using a Stat panel when historical trends are required. In such cases, a Time Series panel is more appropriate.

---

### Question 4

**Question**

When would you use a Gauge panel?

**Answer**

A Gauge panel displays a metric as a percentage or value within a defined range.

**Explanation**

It helps determine whether a metric is within acceptable thresholds.

**Where it is used in Production**

- CPU utilization
- Memory usage
- Disk utilization
- Database connection usage

---

### Question 5

**Question**

What is a Table panel, and when is it useful?

**Answer**

A Table panel displays query results in rows and columns instead of graphical charts.

**Explanation**

It is useful when detailed information is more important than trends.

**Where it is used in Production**

- Pod status
- Alert lists
- Host inventory
- Service status
- Log summaries

---

### Question 6

**Question**

When would you use a Bar Chart or Pie Chart panel?

**Answer**

- **Bar Chart:** Compares values across different categories.
- **Pie Chart:** Shows the percentage contribution of each category to the total.

**Explanation**

These visualizations help compare resource usage, error distribution, or request counts.

**Where it is used in Production**

- Resource usage by server
- Error type distribution
- Request distribution
- Service comparison

**Common Mistake**

Using Pie Charts for large datasets, making the visualization difficult to interpret.

---

### Question 7

**Question**

What is the Query Editor in Grafana?

**Answer**

The Query Editor is the interface used to write and execute queries against a configured data source.

**Explanation**

The query language depends on the selected data source. For Prometheus, the Query Editor uses PromQL.

**Where it is used in Production**

Building dashboards, alerts, and custom visualizations.

---

### Question 8

**Question**

What is PromQL, and why is it important in Grafana?

**Answer**

PromQL (Prometheus Query Language) is the query language used to retrieve and manipulate metrics stored in Prometheus.

**Explanation**

Grafana sends PromQL queries to Prometheus and visualizes the returned results.

**Where it is used in Production**

- CPU monitoring
- Memory monitoring
- Kubernetes monitoring
- Application performance monitoring

**Common Mistake**

Assuming Grafana has its own query language. Grafana uses the query language supported by the configured data source.

---

### Question 9

**Question**

Why is time range selection important in Grafana?

**Answer**

Time range selection determines the period over which Grafana retrieves and displays data.

Examples include:

- Last 5 minutes
- Last 1 hour
- Last 24 hours
- Last 7 days

**Explanation**

Choosing the correct time range helps analyze recent issues or long-term performance trends.

**Where it is used in Production**

Investigating incidents, outages, and capacity planning.

---

### Question 10

**Question**

What are filters in Grafana queries?

**Answer**

Filters limit query results by selecting only the required metrics or labels.

Examples:

- Specific server
- Namespace
- Pod
- Cluster
- Environment

**Explanation**

Filters reduce unnecessary data and improve dashboard readability.

**Where it is used in Production**

Large-scale environments with hundreds or thousands of monitored resources.

---

### Question 11

**Question**

What are aggregation functions in PromQL?

**Answer**

Aggregation functions combine multiple metric values into a single result.

Common functions include:

- sum()
- avg()
- max()
- min()
- count()

**Explanation**

Aggregations simplify monitoring by providing summarized information instead of individual metrics.

**Where it is used in Production**

- Average CPU utilization
- Total request count
- Maximum memory usage
- Cluster-wide statistics

**Common Mistake**

Using raw metrics instead of aggregated values when monitoring large environments.

---

### Question 12

**Question**

How do you create a Grafana panel using Prometheus?

**Answer**

The typical process is:

1. Create a dashboard.
2. Add a panel.
3. Select Prometheus as the data source.
4. Write a PromQL query.
5. Choose a visualization type.
6. Configure legends and thresholds.
7. Save the dashboard.

**Explanation**

Each panel retrieves data independently from Prometheus and visualizes it according to the selected chart type.

**Where it is used in Production**

Creating infrastructure and application monitoring dashboards.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

A dashboard shows "No Data" for one panel, while other panels work correctly. How would you troubleshoot it?

**Answer**

I would:

- Verify the PromQL query.
- Check the selected data source.
- Confirm metric availability.
- Verify the dashboard time range.
- Review query filters.

**Explanation**

The issue is usually related to the panel query rather than Grafana itself.

---

### Scenario 2

**Question**

Your manager wants to monitor CPU utilization trends for the past 30 days. Which panel would you use and why?

**Answer**

I would use a **Time Series** panel because it displays metric changes over time and makes trends easy to analyze.

**Explanation**

Historical performance analysis requires time-based visualization.

---

### Scenario 3

**Question**

A dashboard displays current CPU usage only. Which visualization would you recommend?

**Answer**

I would recommend either:

- Stat Panel
- Gauge Panel

depending on whether a numeric value or threshold visualization is preferred.

**Explanation**

These panels provide quick visibility into the current metric value.

---

### Scenario 4

**Question**

A dashboard takes several seconds to load because one panel executes a complex query. How would you optimize it?

**Answer**

I would:

- Simplify the query.
- Use aggregation functions.
- Reduce the queried time range.
- Apply filters.
- Use recording rules if available.

**Explanation**

Complex queries against large datasets significantly increase dashboard load times.

---

### Scenario 5

**Question**

A dashboard needs to display CPU usage for only the Production environment. How would you implement this?

**Answer**

I would filter the PromQL query using environment labels or create a dashboard variable for environment selection.

**Explanation**

Label filtering retrieves only the required metrics.

---

### Scenario 6

**Question**

A user accidentally selects a 90-day time range, causing dashboards to load slowly. What would you recommend?

**Answer**

I would configure a reasonable default time range, such as the last 1 hour or last 24 hours, and educate users to use larger ranges only when necessary.

**Explanation**

Large time ranges increase query execution time and data retrieval.

---

### Scenario 7

**Question**

Your application team wants to compare CPU usage across five Kubernetes nodes. Which visualization would you recommend?

**Answer**

I would use a **Bar Chart** because it clearly compares values across multiple nodes.

**Explanation**

Bar Charts are ideal for comparing categories.

---

### Scenario 8

**Question**

Your manager asks for the percentage of requests served by each application. Which panel would you use?

**Answer**

I would use a **Pie Chart** because it shows proportional distribution across applications.

**Explanation**

Pie Charts effectively visualize percentage-based comparisons.

---

### Scenario 9

**Question**

A panel displays incorrect values after changing the PromQL query. What would you verify?

**Answer**

I would:

- Validate the query syntax.
- Confirm metric names.
- Verify labels.
- Test the query directly in Prometheus.
- Review aggregation functions.

**Explanation**

Most incorrect values result from invalid queries or incorrect label selection.

---

### Scenario 10

**Question**

Your manager wants a dashboard that allows switching between different Kubernetes clusters without creating multiple dashboards. How would you implement it?

**Answer**

I would create dashboard variables for cluster selection and reference those variables in all PromQL queries.

**Explanation**

Dashboard variables make dashboards reusable across multiple environments while reducing maintenance effort.
