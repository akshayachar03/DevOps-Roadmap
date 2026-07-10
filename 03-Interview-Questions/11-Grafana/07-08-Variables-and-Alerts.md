# Variables & Alerts Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What are dashboard variables in Grafana?

**Answer**

Dashboard variables are dynamic placeholders that allow users to filter and reuse dashboards without modifying the underlying queries.

**Explanation**

Instead of creating separate dashboards for each server, cluster, or environment, variables allow users to select the desired value from a dropdown menu. Grafana automatically substitutes the selected value into the query.

**Where it is used in Production**

- Switching between servers
- Monitoring multiple Kubernetes clusters
- Selecting namespaces
- Choosing environments (Dev, QA, Production)

**Common Mistake**

Creating multiple dashboards for different servers instead of using variables.

---

### Question 2

**Question**

What is a Query Variable in Grafana?

**Answer**

A Query Variable retrieves its values dynamically from the configured data source.

**Explanation**

For example, a Prometheus query can automatically populate a list of available Kubernetes namespaces or node names. When new resources are added, the dropdown updates automatically without modifying the dashboard.

**Where it is used in Production**

- Server selection
- Kubernetes namespaces
- Pods
- Clusters
- Applications

---

### Question 3

**Question**

What is a Custom Variable?

**Answer**

A Custom Variable contains manually defined values instead of retrieving them from a data source.

**Explanation**

The administrator specifies a predefined list of values such as:

- Development
- Testing
- Production

These values remain static until manually updated.

**Where it is used in Production**

- Environment selection
- Region selection
- Team selection
- Application categories

**Common Mistake**

Using Custom Variables for frequently changing resources instead of Query Variables.

---

### Question 4

**Question**

How are variables used inside Grafana queries?

**Answer**

Variables are referenced inside queries using the variable syntax.

For example:

- Select a server
- Select a namespace
- Select an application

Grafana replaces the variable with the selected value before executing the query.

**Explanation**

This allows a single dashboard to support multiple resources dynamically.

**Where it is used in Production**

Reusable infrastructure and Kubernetes monitoring dashboards.

---

### Question 5

**Question**

Why are dashboard variables important in large production environments?

**Answer**

Variables reduce dashboard duplication and simplify maintenance.

**Explanation**

Instead of maintaining hundreds of dashboards for different servers or clusters, organizations maintain one dashboard that dynamically adapts using variables.

**Where it is used in Production**

Large cloud environments with hundreds or thousands of monitored resources.

---

### Question 6

**Question**

What is Grafana Alerting?

**Answer**

Grafana Alerting continuously evaluates monitoring data and generates alerts when configured conditions are met.

**Explanation**

Grafana periodically executes alert queries against the configured data source. If the alert condition evaluates to true, a notification is generated.

**Where it is used in Production**

- High CPU utilization
- Low disk space
- Application downtime
- High memory usage
- Service failures

---

### Question 7

**Question**

What is an Alert Rule in Grafana?

**Answer**

An Alert Rule defines:

- The query to evaluate
- The evaluation interval
- The alert condition
- The notification behavior

**Explanation**

Alert rules automate monitoring by checking metrics continuously without manual intervention.

**Where it is used in Production**

Infrastructure, applications, Kubernetes, databases, and cloud services.

---

### Question 8

**Question**

What is an Alert Condition?

**Answer**

An Alert Condition defines the threshold that determines whether an alert should be triggered.

Examples include:

- CPU > 80%
- Memory > 90%
- Disk usage > 95%
- HTTP error rate > 5%

**Explanation**

Grafana evaluates these conditions at regular intervals.

**Where it is used in Production**

Proactive infrastructure monitoring.

---

### Question 9

**Question**

What is Alert Evaluation?

**Answer**

Alert Evaluation is the process of executing alert rules at fixed intervals to determine whether alert conditions are satisfied.

**Explanation**

Grafana periodically queries the data source and compares the returned values against the configured thresholds.

**Where it is used in Production**

Continuous monitoring of infrastructure and applications.

**Common Mistake**

Assuming alerts are evaluated continuously. They run according to the configured evaluation interval.

---

### Question 10

**Question**

What are Notification Policies in Grafana?

**Answer**

Notification Policies determine how alerts are grouped, routed, and delivered to the appropriate recipients.

**Explanation**

Policies allow organizations to route different alerts to different teams based on severity, application, or environment.

**Where it is used in Production**

- DevOps team notifications
- Database team alerts
- Kubernetes alerts
- Application support alerts

---

### Question 11

**Question**

What are Contact Points in Grafana?

**Answer**

Contact Points define where alert notifications are sent.

Examples include:

- Email
- Slack
- Microsoft Teams
- PagerDuty
- Webhooks
- Discord

**Explanation**

When an alert is triggered, Grafana sends the notification to the configured contact point.

**Where it is used in Production**

Incident management and operational monitoring.

---

### Question 12

**Question**

How do variables and alerts work together in Grafana?

**Answer**

Variables are used for dashboard filtering, while alerts are evaluated against fixed queries. Alert rules generally use explicit values rather than dashboard variables because alerts must execute automatically without user interaction.

**Explanation**

Dashboard variables improve visualization, whereas alerts require consistent and deterministic evaluation.

**Where it is used in Production**

Enterprise monitoring environments with reusable dashboards and automated alerting.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your company has 500 Linux servers. How would you avoid creating 500 separate dashboards?

**Answer**

I would create a single dashboard with a Query Variable that dynamically lists all servers.

**Explanation**

Variables make dashboards reusable and significantly reduce maintenance effort.

---

### Scenario 2

**Question**

A newly deployed Kubernetes namespace does not appear in the dashboard variable list. What would you check?

**Answer**

I would verify:

- The Query Variable configuration.
- The Prometheus query.
- Metric availability.
- Dashboard refresh settings.
- Variable refresh option.

**Explanation**

Query Variables depend on the data source returning the latest values.

---

### Scenario 3

**Question**

Your manager wants CPU alerts only for production servers. How would you implement this?

**Answer**

I would configure alert queries with filters that include only production labels or production-specific metrics.

**Explanation**

Filtering prevents unnecessary alerts from development or testing environments.

---

### Scenario 4

**Question**

Users report receiving duplicate alert notifications. What would you investigate?

**Answer**

I would check:

- Notification Policies.
- Contact Point configuration.
- Duplicate Alert Rules.
- Alert grouping configuration.
- Evaluation intervals.

**Explanation**

Duplicate rules or incorrect routing commonly cause repeated notifications.

---

### Scenario 5

**Question**

A CPU alert is not triggering even though CPU utilization exceeds 90%. What would you troubleshoot?

**Answer**

I would verify:

- Alert Rule configuration.
- Alert Condition.
- Query correctness.
- Evaluation interval.
- Metric availability.
- Threshold values.

**Explanation**

Most alert failures are caused by incorrect queries or misconfigured thresholds.

---

### Scenario 6

**Question**

Your team wants critical alerts sent to PagerDuty while warning alerts should go to Slack. How would you configure this?

**Answer**

I would create separate Notification Policies with different Contact Points based on alert severity.

**Explanation**

Notification Policies allow alerts to be routed to different destinations automatically.

---

### Scenario 7

**Question**

An alert continues firing even after CPU usage returns to normal. What would you check?

**Answer**

I would verify:

- Alert recovery conditions.
- Evaluation interval.
- Query accuracy.
- Metric freshness.
- Alert state history.

**Explanation**

Delayed metric updates or incorrect alert thresholds can prevent alerts from resolving.

---

### Scenario 8

**Question**

A dashboard variable shows duplicate server names. How would you troubleshoot it?

**Answer**

I would review:

- The Query Variable.
- Returned labels.
- Prometheus target labels.
- Duplicate scrape configurations.
- Metric uniqueness.

**Explanation**

Duplicate labels in the monitoring system often result in duplicate variable values.

---

### Scenario 9

**Question**

Your organization wants all infrastructure alerts sent to the Infrastructure team and application alerts sent to the Application Support team. How would you implement this?

**Answer**

I would configure separate Notification Policies based on labels and assign different Contact Points for each team.

**Explanation**

Label-based routing ensures alerts reach the correct operational team.

---

### Scenario 10

**Question**

Your manager asks for a single dashboard that allows switching between Development, QA, and Production environments. How would you implement it?

**Answer**

I would create an environment variable (Query Variable or Custom Variable) and reference it in all dashboard queries.

**Explanation**

Using variables makes the dashboard reusable across environments while reducing duplication and simplifying maintenance.
