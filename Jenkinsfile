#!/usr/bin/env groovy

node {
    try {
        stage ('scm') {
            checkout scm
        }

        stage ('build') {
            sh "${tool 'maven-3.3.9'}/bin/mvn -B clean verify"
        }

    } finally {
        step([$class: 'InfluxDbPublisher',
          target: 'http://influxdb:8086,jenkinsdb'])
    }
}
