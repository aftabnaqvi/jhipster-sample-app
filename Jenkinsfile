pipeline {
  agent any
  stages {
    stage('Checking out code') {
      steps {
          sh 'echo cloning repo'
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'Github-password', url: 'https://github.com/aftabnaqvi/jhipster-sample-app.git']]])
      }
    }
    stage('Build') {
      steps {
        sh 'echo Build'
        mvnw -Pprod clean package
      }
    }
    stage('Backend') {
      steps {
        parallel(
          "Unit Test": {
            sh 'echo Unit'
            
          },
          "Performance": {
            sh 'echo Performance'
            
          }
        )
      }
    }
    stage('Frontend') {
      steps {
        sh 'echo Frontend'
      }
    }
    stage('Static Analysis') {
      steps {
        sh 'echo Static Analysis'
      }
    }
    stage('Deployment') {
      steps {
        sh 'echo Deployment'
      }
    }
  }
}
