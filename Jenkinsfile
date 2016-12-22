#!/usr/bin/env groovy

node {
    try {
        stage ('scm') {
            checkout scm
        }

        stage ('build') {
            sh "${tool 'maven-3.3.9'}/bin/mvn -B clean verify"
            currentBuild.result = 'SUCCESS'
        }

    } catch (Exception err) {
        currentBuild.result = 'FAILURE'
    }
    finally {
        def myBuildInfo = [:]
        def myCustomDataMap = [:]
        def build_status_numeric = 0
        if (currentBuild.result == 'FAILURE') {
            build_status_numeric = 1
        }

        myBuildInfo["build_status_message"] = currentBuild.result
        myBuildInfo["build_status_numeric"] = build_status_numeric
        myCustomDataMap["jenkins_data"] = myBuildInfo

        step([$class: 'InfluxDbPublisher',
              target: 'http://influxdb:8086,jenkinsdb',
              customDataMap: myCustomDataMap])
    }
}
