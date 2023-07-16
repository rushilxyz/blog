---
title: To Build A Data Project
slug: practical-letter-on-data
date_published: 2022-12-06T04:12:56.000Z
date_updated: 2022-12-06T04:12:55.000Z
tags: Blog
---

Good Evening,

My letters to you have been too philosophical. Let's counteract that with something practical. Today's letter will be on data architecture. Exciting, I know. I've been building an internal project at work for this past month while traveling. The rest of this letter will be in a case study format to formalize my explanation. 

## The Backstory

The purpose of this project is to utilize manufacturing data to help the industry with preventative maintenance. By forecasting failures in manufacturing machinery, supply chains can prevent input problems before they happen. This helps optimize production output by limiting errors. What does that mean? Let's use a fictitious manufacturing business to break it down:
![](__GHOST_URL__/content/images/2022/12/image-5.png)
For this demonstration, let's simplify the infographic:

- Zant Automotive has 2 manufacturing plants
- Each plant has 3 assembly lines, consisting of 4 machines per assembly line
- The machines have 4 in-built sensors (e.g. temperature, fan speed, pressure, and vibration)
- The sensors will collect and store data per second for anomaly detection

Before the technical talk, this is what anomalies from sensor data would look like:
![](__GHOST_URL__/content/images/2022/12/image-6.png)
Now for the fun part, how the backend is built to display said dashboard.

## Sensor Anomaly Detection

Keep in mind, this is simulated. I've written a script in C# to stream simulated sensor data to be stored in a database. This is the output of the code:
![](__GHOST_URL__/content/images/2022/12/image-7.png)My laptop screen isn't wide enough :(
The sensor values in the database look like this:
![](__GHOST_URL__/content/images/2022/12/image-8.png)
As mentioned, we see four sensor values categorized by the plant, assembly, and machine they're placed in. This is still raw data that provides no information. Our purpose is to extract insight from this dataset. Since it comes with a timestamp, we can query the table and detect anomalies within certain periods. I scripted a basic anomaly detection query as an example:
![](__GHOST_URL__/content/images/2022/12/image-10.png)
- The query takes sensor values for the past 5 minutes
- It separates values by specifying which plant, assembly, machine, and sensor to analyze 
- The actual anomaly detection is done through the `[series_decompose_anomalies](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/series-decompose-anomaliesfunction#syntax)` function, which autodetects a baseline that captures a repetitive pattern
- The outliers detected are rendered in a chart, along with normal values

This is cool, but the process to query the data is manual. How should we go about automating this process to detect sensor anomalies within every manufacturing plant, assembly, and machine? 

## Data Pipeline Demo

In a computing context, a pipeline is a linear sequence of instructions designed to automate software execution. In our case, the anomaly detection query will be configured in a pipeline to analyze every plant, assembly, machine, and sensor value every 5 minutes. Here's the summary of how the data pipeline is set up:
![](__GHOST_URL__/content/images/2022/12/image-11.png)There's much more complexity involving this pipeline, but we'll skip revealing the secret sauce
It's designed to execute the query four times for each sensor within each plant, assembly, and machine. Once an anomaly is detected, new tables are created to form a new dataset to provide better insight. The output for this current pipeline copies data to a Customer Relationship Management (CRM) system. It comes in the form of an alert to inform manufacturing employees an anomaly has been detected. Here's an output as an example of what the alert would look like:
![](__GHOST_URL__/content/images/2022/12/image-12.png)
Of course, now that the pipeline can copy insight to a CRM tool, many interesting things can happen:

- New pipelines/processes/flows can be created to alert technicians for inspection
- Emails can be sent out to necessary stakeholders in the manufacturing plant
- All historical data can be set into a machine learning model to detect anomalies before they even happen, better yet provide solutions to eliminate them entirely

## Conclusion

The purpose of this demo is to showcase the possible use cases for manufacturing data. Not only can the industry benefit from gathering such insight, but actionable alerting systems can be set up optimize performance. 

To be completely honest, I never saw a market for this when I initially built this project. After my trip to Vietnam, I witnessed hundreds of manufacturing machines that could benefit from similar data pipelines. This project is still in its infancy. The purpose is to demonstrate the potential. There's a market for this type of work and the goal of this case study is breakdown what's possible.

I enjoy the randomness of the letters you receive. It keeps writing them more fun.

-rushil :)
