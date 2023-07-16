---
title: Demystifying Data
slug: demystifying-data
date_published: 2022-09-13T02:52:01.000Z
date_updated: 2022-09-13T02:52:01.000Z
tags: Blog
---

Good Evening,

The purpose of this newsletter is to demystify what I do for a living. I transfer data from one place to another and make use of it. At least, that's what I think a data engineer is supposed to do. 

This is to showcase an end-to-end solution using Azure Synapse and PowerBi. It's a project meant to take manufacturing data and help the industry with preventative maintenance. 

I have a diagram here to give some context on the process:
![](__GHOST_URL__/content/images/2022/09/image.png)
What we're trying to solve for is to detect anomalies in sensor data to send out alerts and prevent future maintenance troubles from happening. Imagine this:

- IoT sensors (connect directly to the internet) are placed on machines in manufacturing plants
- They will collect telemetry data like temperature, fan speed, pressure, or vibration sensitivity
- The data would get streamed and ingested into IoT Hub 
- Azure synapse is where the anomalies would get detected, which also triggers an email alert
- The transformed data from synapse is also integrated into PowerBi to view the data in a convenient dashboard

Now for the fun part. 

I have no sensors for the purpose of this demo, so I have some Visual Studio code to simulate temperature readings. The data is directly streamed into IoT hub. Here's a snippet of the code for the simulated data for those who are curious:

        private static async Task SendAnomalyMessagesAsync()
        {
            // Initial telemetry values
            double minTemperature = 20;
            var rand = new Random();
            int i = 0;
    
            string sensorID = "S001LM35";
            DateTime ingestionTimeStamp = DateTime.Now;
            double currentTemperature = minTemperature + rand.NextDouble() * 15;
            string building = "B-WING";
            string buildingType = "Office";
            string city = "Toronto";
            string street = "8 York Street";
            string state = "Ontario";
            string country = "Canada";
    
            int randomSequenceLength = rand.Next(1,10);
    
            while (i < randomSequenceLength)
            {
                currentTemperature = rand.Next(150, 200);
    
                // Create JSON message
                string messageBody = JsonSerializer.Serialize(
                new
                {
                    deviceId = sensorID,
                    timestamp = ingestionTimeStamp,
                    temperature = currentTemperature,
                    building = building,
                    buildingType = buildingType,
                    city = city,
                    street = street,
                    state = state,
                    country = country,
    
                });
                using var message = new Message(Encoding.ASCII.GetBytes(messageBody))
                {
                    ContentType = "application/json",
                    ContentEncoding = "utf-8",
                };
    
                message.Properties.Add("temperatureAlert", (currentTemperature > 30) ? "true" : "false");
    
                // Send the telemetry message
                await s_deviceClient.SendEventAsync(message);
                Console.WriteLine($"{DateTime.Now.ToUniversalTime()} > Sending message: {messageBody}");
                await Task.Delay(1000);
                i++;
            }
        }
    }
    

This is what the output of the simulated temperature data sensor looks like. It creates a new reading every second (like an actual sensor typically would):
![](__GHOST_URL__/content/images/2022/09/image-1.png)
There are normal temperature readings ranging between 20-30 degrees. Anomalies are randomly introduced using the code above, which go from 150-200 degrees. The simulated raw data is directly streamed into IoT hub. 

This is what the data looks like:
![](__GHOST_URL__/content/images/2022/09/image-6.png)
Let's see what happens to the data when it enters synapse. Azure Data Explorer has a KQL query language similar to SQL that can organize the data being streamed into IoT hub. The anomalies can be detected from the following query:
![](__GHOST_URL__/content/images/2022/09/image-2.png)
As you can see, the query detects the temperature readings above 30 degrees as anomalies. The chart is used to record a timestamp on when the anomaly was detected. Email alerts are set-up through a synapse pipeline:
![](__GHOST_URL__/content/images/2022/09/image-3.png)
The outputs from the anomaly detector query are run through a Boolean condition to check if anomalies exist. If the count is not 0, an email gets triggered.  It's designed to run every 5 minutes and send an email if anomalies are detected. 

As for PowerBi integration, that's still a work in progress. This should give an idea on how the dashboards would be set-up for the different sensors:
![](__GHOST_URL__/content/images/2022/09/image-5.png)
Hopefully this demystified how data in the backend gets transformed into a useful frontend (which is what you typically see). I plan to work on more projects like this to convince myself (and you) that data isn't boring. 

Until next time,
-rushil
