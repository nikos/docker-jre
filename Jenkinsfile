pipeline {
  agent any
  triggers {
    upstream(
      upstreamProjects: "docker/development-base/master",
      threshold: hudson.model.Result.SUCCESS
    )
  }  
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
          def image = docker.build('n7lab/jdk:8', 'jdk8')
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
        script {
          def image = docker.build('n7lab/jdk:9', 'jdk9')
          image.push('latest' + env.BUILD_NUMBER)
          image.push('9')
          image.push('9-' + env.BUILD_NUMBER)
        }
      }
    }
  } 
}