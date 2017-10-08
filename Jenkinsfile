pipeline {
  agent any
  stages {
    stage('Build and push Docker images') {
      steps {
        script {
          def image = docker.build('n7lab/jre:8', 'jre8')
          image.push('8')
          image.push('8u144')
          image.push('8u144-' + env.BUILD_NUMBER)
        }
        script {
          def image = docker.build('n7lab/jre:9', 'jre9')
          image.push('latest' + env.BUILD_NUMBER)
          image.push('9')
          image.push('9-' + env.BUILD_NUMBER)
        }
      }
    }
  } 
}