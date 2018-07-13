pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        deleteDir()
        checkout scm
      }
    }
    stage('Build') {
      steps {
        script {
          sh 'npm install'
          commitChanges()
        }
      }
    }
    stage('Unit Test') {
      steps {
        script {
          sh 'npm test'
        }
      }
    }
  }
}