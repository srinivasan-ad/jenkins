pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/srinivasan-ad/Jenkins.git', branch: 'main'
      }
    }
    stage('Build') {
      steps {
        sh './gradlew clean build'
      }
    }
    stage('Test') {
      steps {
        sh './gradlew test'
      }
    }
  }
  post {
    always {
      junit '**/build/test-results/test/*.xml'
    }
    success {
      echo 'Build and tests succeeded!'
    }
    failure {
      echo 'Build or tests failed.'
    }
  }
}
