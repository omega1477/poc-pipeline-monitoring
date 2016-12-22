#!/usr/bin/env groovy

node {
    stage ('scm') {
        checkout scm
    }

    stage ('build') {
        sh "${tool 'maven-3.3.9'}/bin/mvn -B clean verify"
    }
}
