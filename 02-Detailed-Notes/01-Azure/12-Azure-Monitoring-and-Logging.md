# Monitoring & Logging in Azure

## Definition

- Monitoring and Logging in Azure help track the health, performance, availability, and security of Azure resources and applications.
- Azure collects metrics, logs, and events to identify issues, troubleshoot problems, and optimize performance.
- The core monitoring service is **Azure Monitor**.

---

## Why is it used?

- Monitor resource health.
- Detect application issues.
- Troubleshoot problems quickly.
- Improve performance.
- Receive alerts for critical events.
- Analyze historical data.

---

## Key Features

- Real-time monitoring.
- Centralized logging.
- Performance metrics.
- Alert notifications.
- Dashboards and Workbooks.
- Application monitoring.
- Log Analytics integration.

---

## Advantages

- Centralized monitoring.
- Early problem detection.
- Faster troubleshooting.
- Better resource optimization.
- Supports automation.

---

## Disadvantages

- Large log collection can increase costs.
- Requires proper monitoring strategy.

---

## Components

- Azure Monitor
- Metrics
- Logs
- Alerts
- Log Analytics Workspace
- Application Insights
- Action Groups
- Diagnostic Settings
- Workbooks

---

## Workflow

```text
Azure Resources
        ↓
Azure Monitor
        ↓
Collect Metrics & Logs
        ↓
Log Analytics Workspace
        ↓
Alerts / Dashboards / Workbooks
```

---

## Real-world Example

A company monitors Virtual Machines, Storage Accounts, and Web Apps using Azure Monitor. If CPU usage exceeds 80%, Azure Monitor sends an email to administrators.

---

## Interview Tip

"Azure Monitor is the central monitoring service that collects metrics and logs from Azure resources and applications."

---

## Quick Revision

- Central monitoring service.
- Collects metrics and logs.
- Supports alerts.
- Integrates with Log Analytics.
- Uses Application Insights for applications.
- Provides dashboards and reports.

---

## Important Interview Questions

1. What is Azure Monitoring?
2. What services are included in Azure Monitoring?
3. Why is monitoring important?
4. What data does Azure Monitor collect?
5. How does Azure Monitor improve operations?

---

# Azure Monitor

## Definition

- Azure Monitor is Microsoft's centralized monitoring platform.
- It collects, analyzes, and visualizes telemetry from Azure resources, applications, and virtual machines.

---

## Why is it used?

- Monitor Azure resources.
- Analyze performance.
- Detect failures.
- Generate alerts.
- Troubleshoot applications.
- Collect logs and metrics.

---

## Key Features

- Metrics collection.
- Log collection.
- Alert rules.
- Dashboards.
- Workbooks.
- Integration with Application Insights.
- Log Analytics integration.

---

## Advantages

- Centralized monitoring.
- Real-time visibility.
- Highly scalable.
- Easy integration.
- Supports automation.

---

## Disadvantages

- Advanced monitoring increases log storage costs.
- Requires alert tuning.

---

## Components

- Metrics
- Logs
- Alerts
- Diagnostic Settings
- Workbooks
- Action Groups

---

## Workflow

```text
Azure Resources
        ↓
Azure Monitor
        ↓
Metrics + Logs
        ↓
Alert Rules
        ↓
Notification
```

---

## Real-world Example

Azure Monitor detects high CPU usage on a Virtual Machine and automatically triggers an alert.

---

## Interview Tip

"Azure Monitor is the central service for collecting, analyzing, and acting on monitoring data."

---

## Quick Revision

- Central monitoring platform.
- Collects metrics.
- Collects logs.
- Generates alerts.
- Uses Log Analytics.
- Supports dashboards.

---

## Important Interview Questions

1. What is Azure Monitor?
2. What data does Azure Monitor collect?
3. How does Azure Monitor work?
4. What services integrate with Azure Monitor?
5. Why is Azure Monitor important?

---

# Log Analytics Workspace

## Definition

- Log Analytics Workspace is a centralized repository where Azure Monitor stores and analyzes log data.
- It uses the Kusto Query Language (KQL) to search and analyze logs.

---

## Why is it used?

- Store logs.
- Analyze resource activity.
- Troubleshoot issues.
- Create reports.
- Support security investigations.

---

## Key Features

- Central log storage.
- Kusto Query Language (KQL).
- Fast searching.
- Integration with Azure Monitor.
- Supports Workbooks.

---

## Advantages

- Centralized logging.
- Powerful querying.
- Long-term log retention.
- Supports multiple Azure services.

---

## Disadvantages

- Large log retention increases costs.
- KQL requires learning.

---

## Workflow

```text
Azure Monitor
      ↓
Log Analytics Workspace
      ↓
KQL Query
      ↓
Results
```

---

## Real-world Example

An administrator runs a KQL query to find all failed login attempts across Azure Virtual Machines.

---

## Interview Tip

"Log Analytics Workspace stores Azure Monitor logs and allows querying them using Kusto Query Language."

---

## Quick Revision

- Central log repository.
- Uses KQL.
- Stores monitoring data.
- Supports Workbooks.
- Integrates with Azure Monitor.

---

## Important Interview Questions

1. What is Log Analytics Workspace?
2. What language is used to query logs?
3. Why is Log Analytics required?
4. How does Log Analytics work with Azure Monitor?
5. What type of data is stored?

---

# Application Insights

## Definition

- Application Insights is an Application Performance Monitoring (APM) service.
- It monitors the availability, performance, and usage of web applications and APIs.

---

## Why is it used?

- Detect application failures.
- Monitor performance.
- Analyze user behavior.
- Identify slow requests.
- Troubleshoot exceptions.

---

## Key Features

- Performance monitoring.
- Exception tracking.
- Live Metrics.
- Availability tests.
- Dependency monitoring.
- Distributed tracing.

---

## Advantages

- Detailed application insights.
- Easy troubleshooting.
- Real-time monitoring.
- Integration with Azure Monitor.

---

## Disadvantages

- Requires application instrumentation.
- High telemetry volume increases cost.

---

## Workflow

```text
Application
      ↓
Application Insights SDK
      ↓
Azure Monitor
      ↓
Performance Dashboard
```

---

## Real-world Example

An e-commerce website identifies a slow checkout page using Application Insights and reduces response time.

---

## Interview Tip

"Application Insights monitors application performance, user requests, exceptions, and dependencies."

---

## Quick Revision

- APM solution.
- Performance monitoring.
- Exception tracking.
- Dependency tracking.
- Availability testing.

---

## Important Interview Questions

1. What is Application Insights?
2. What is APM?
3. What information does Application Insights collect?
4. How does it integrate with Azure Monitor?
5. What is Live Metrics?

---

# Azure Alerts

## Definition

- Azure Alerts notify administrators when specified conditions occur.
- Alerts can be created using metrics, logs, or activity logs.

---

## Why is it used?

- Detect problems quickly.
- Notify administrators.
- Automate responses.
- Prevent downtime.

---

## Key Features

- Metric alerts.
- Log alerts.
- Activity Log alerts.
- Smart alerts.
- Multiple notification methods.

---

## Advantages

- Early issue detection.
- Automatic notifications.
- Supports automation.
- Reduces downtime.

---

## Disadvantages

- Poorly configured alerts create alert fatigue.
- Too many alerts can be difficult to manage.

---

## Workflow

```text
Metric/Log
      ↓
Alert Rule
      ↓
Action Group
      ↓
Email/SMS/Webhook
```

---

## Real-world Example

If CPU usage exceeds 85% for 10 minutes, Azure Monitor sends an email and triggers an automation runbook.

---

## Interview Tip

"Alerts notify administrators when Azure resources meet predefined conditions."

---

## Quick Revision

- Metric Alerts.
- Log Alerts.
- Activity Log Alerts.
- Action Groups.
- Automatic notifications.

---

## Important Interview Questions

1. What are Azure Alerts?
2. What types of alerts exist?
3. What is an Alert Rule?
4. What is an Action Group?
5. Why are alerts important?

---

# Azure Metrics

## Definition

- Metrics are numerical values collected at regular intervals that describe the health and performance of Azure resources.

---

## Why is it used?

- Monitor performance.
- Detect resource bottlenecks.
- Create alerts.
- Visualize trends.

---

## Key Features

- Near real-time data.
- Time-series data.
- Lightweight.
- Supports dashboards.

---

## Common Metrics

- CPU Percentage
- Memory Usage
- Disk IOPS
- Network In/Out
- Requests Per Second
- Response Time

---

## Real-world Example

A VM's CPU utilization is monitored every minute to identify performance issues.

---

## Interview Tip

"Metrics provide numerical performance data collected at regular intervals."

---

## Quick Revision

- Numerical data.
- Near real-time.
- Performance monitoring.
- Used in alerts.
- Lightweight.

---

## Important Interview Questions

1. What are Azure Metrics?
2. What are common VM metrics?
3. How often are metrics collected?
4. Why are metrics useful?
5. Difference between Metrics and Logs?

---

# Azure Logs

## Definition

- Logs contain detailed records of events and operations performed by Azure resources and applications.

---

## Why is it used?

- Troubleshooting.
- Auditing.
- Security analysis.
- Performance investigation.

---

## Key Features

- Detailed information.
- Searchable using KQL.
- Stored in Log Analytics Workspace.
- Long-term retention.

---

## Types

- Resource Logs
- Activity Logs
- Application Logs
- Security Logs

---

## Real-world Example

An administrator checks Activity Logs to determine who deleted a Virtual Machine.

---

## Interview Tip

"Logs provide detailed event information, while metrics provide numerical performance data."

---

## Quick Revision

- Detailed event records.
- KQL queries.
- Long-term storage.
- Supports auditing.
- Used for troubleshooting.

---

## Important Interview Questions

1. What are Azure Logs?
2. What is the difference between Metrics and Logs?
3. Where are logs stored?
4. What are Activity Logs?
5. How are logs queried?

---

# Diagnostic Settings

## Definition

- Diagnostic Settings control where Azure resource logs and metrics are sent for storage and analysis.

---

## Why is it used?

- Export logs.
- Store monitoring data.
- Enable auditing.
- Support security monitoring.

---

## Key Features

- Send data to Log Analytics.
- Archive to Storage Account.
- Stream to Event Hub.
- Resource-specific configuration.

---

## Workflow

```text
Azure Resource
      ↓
Diagnostic Settings
      ↓
Log Analytics / Storage / Event Hub
```

---

## Real-world Example

Diagnostic Settings send NSG flow logs to Log Analytics Workspace for security analysis.

---

## Interview Tip

"Diagnostic Settings define where Azure resource logs and metrics are collected."

---

## Quick Revision

- Collects logs.
- Sends metrics.
- Supports Storage.
- Supports Event Hub.
- Supports Log Analytics.

---

## Important Interview Questions

1. What are Diagnostic Settings?
2. Where can diagnostic data be sent?
3. Why are Diagnostic Settings required?
4. Can every Azure resource have Diagnostic Settings?
5. How are logs collected?

---

# Action Groups

## Definition

- Action Groups define the actions Azure performs when an alert is triggered.

---

## Why is it used?

- Notify administrators.
- Trigger automation.
- Send emails.
- Send SMS.
- Call webhooks.

---

## Key Features

- Email notifications.
- SMS.
- Push notifications.
- Voice calls.
- Azure Automation.
- Logic Apps.
- Webhooks.

---

## Workflow

```text
Alert Triggered
      ↓
Action Group
      ↓
Email / SMS / Automation
```

---

## Real-world Example

When a VM becomes unavailable, Azure sends an email to administrators and triggers an Azure Automation Runbook.

---

## Interview Tip

"Action Groups define what happens after an Azure Alert is triggered."

---

## Quick Revision

- Email.
- SMS.
- Webhook.
- Logic Apps.
- Automation.

---

## Important Interview Questions

1. What is an Action Group?
2. What actions can Action Groups perform?
3. How do Alerts use Action Groups?
4. Can Action Groups trigger automation?
5. Why are Action Groups useful?

---

# Azure Workbooks

## Definition

- Azure Workbooks are interactive dashboards that visualize Azure monitoring and log data.
- They combine charts, tables, metrics, logs, and queries into a single report.

---

## Why is it used?

- Visualize monitoring data.
- Create dashboards.
- Troubleshoot systems.
- Share monitoring reports.
- Analyze trends.

---

## Key Features

- Interactive dashboards.
- KQL integration.
- Charts and graphs.
- Custom reports.
- Azure Monitor integration.

---

## Advantages

- Easy visualization.
- Highly customizable.
- Interactive.
- Supports multiple data sources.

---

## Disadvantages

- Complex dashboards require KQL knowledge.
- Large workbooks may load slowly.

---

## Workflow

```text
Azure Monitor
      ↓
Logs & Metrics
      ↓
Workbook
      ↓
Charts & Reports
```

---

## Real-world Example

A Cloud Operations team creates a Workbook displaying VM CPU usage, application response time, storage utilization, and security alerts on a single dashboard.

---

## Interview Tip

"Azure Workbooks provide customizable dashboards for visualizing Azure monitoring and log data."

---

## Quick Revision

- Interactive dashboards.
- KQL support.
- Charts.
- Reports.
- Azure Monitor integration.

---

## Important Interview Questions

1. What are Azure Workbooks?
2. How are Workbooks different from Dashboards?
3. What data sources can Workbooks use?
4. Can Workbooks use KQL?
5. Why are Workbooks useful?
