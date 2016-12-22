# poc-pipeline-monitoring
POC to create a dashboard for Jenkins Pipelines

**The ideal:**
  - How to monitor Pipelines via jenkins

- Using 
  - http://grafana.org/ or https://graphiteapp.org/
  - Jenkins Pipelines

- To answer the questions:
  - What may be the bottlenecks?
  - What jobs are frequently failing?
  - Is it possible to alert a team based on 3 consecutive failures

- This could be tied to a CI server, github, or rally/jira
  - integrate: nexus server, sonarqube server, etc
  - Open, what other metrics would you like to see on a dashboard if you were a product owner, developer, or in quality?

- Intention: 
  - to remove the user away from Jenkins, and closer to the project to reveal more insightful information in one location
  - To minimize the tools of the average developer
  
  **Notes**
```
1. Using influxdb as a datastorage is eligible (no graphite as a backend and as result no creation of any custom Jenkins plugin from scratch (phew!))
2. As a result for short POC would be enough to send STATUS, DURATION and may be some more job’s meta info into influxdb. Show it in Grafana would be great.
3. It may be done on some custom maven project, which could be shared with my github-id: eugeun
4. Thursday is a deadline for this short POC
```
