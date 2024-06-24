pipeline {
  agent any
  environment {
    brew = "/opt/homebrew/bin/brew"
  }
  stages {
    stage('verify k6') {
      steps {
        sh 'k6 version'
      }
    }
    stage('run k6 test') {
      steps {
        echo 'Installing k6'
        sh 'chmod +x ./setup_k6.sh'
        sh './setup_k6.sh'
        echo 'Running K6 performance tests...'
        sh 'k6 run influxdb=http://192.168.1.48:8086/k6 permance-test.js'
      }
    }
  }
}
