# Monitoring System Performance

Monitoring IT infrastructure provides insight into the health of each asset. This benefits all users because actions can be taken to mitigate potential outages before those happen.

If there is no monitoring, no one has any idea if a server is about to go down or if the application has stopped working. The only way you know comes from the end-users, which is not good.

# Lesson Outline

In this lesson, we will learn how to:

Install and configure a monitoring system using Prometheus and Grafana.
Identify host metrics and create a dashboard with host metrics
Install and configure a synthetic monitoring solution
Create alerts for application metrics
By the end of this lesson, you will have a fully-functional monitoring system that uses some of the most popular tools in the industry.

# How Do Experts Think About Monitoring System Performance?

## Data aggregation & Centralization

Collecting metrics from IT infrastructure
Installing an exporter program to the collect information
Configuring the exporter program to start when the machine starts
Storing it in one place
It makes it easy to manage and configure
You only need one tool to view data

## Dashboarding

Displaying the stored data
Organizing the displayed data
Forming logical groupings of data in charts
e.g., A chart for each metric--latency, saturation, errors, and traffic--displayed on one dashboard

## Alerting

Configuring alerting rules
Categorizing alerts into severity levels
Telling alerts when to fire
Setting up notification groups
Consuming a webhook in a team chat/communication program such as Slack
Creating the alert message itself
What information should the alert contain?

# Prometheus and Grafana

## Prometheus:

Open-source monitoring & alerting toolkit
Aggregates data from IT infrastructure
Alerts can be configured to tell us when data goes above (or below) a set threshold

## Grafana:

Open-source dashboarding software
Presents data in many different ways
Many modules can be used to present the data, which include:
Time-series graphs
Bar-charts
Heatmaps
Gauges
