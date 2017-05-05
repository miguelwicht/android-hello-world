#!/usr/bin/env groovy

node('docker') {
    stage('Checkout code') {
        checkout scm
    }

    stage('Download dependencies') {
        sh 'docker pull mreichelt/android'
    }

    stage('Build') {
        sh "docker run --rm -v ${env.WORKSPACE}:\"/app\" -w=\"/app\" mreichelt/android ./gradlew assembleDebug"
    }

    stage('Archive Artifacts') {
        archiveArtifacts 'app/build/outputs/apk/*.apk'
    }
}