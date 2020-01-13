pipeline {
  agent any

  tools {
    maven "apache-maven-3.6.3"
  }

  stages {
    stage('Build') {
      steps {
        git 'https://github.com/ajlanghorn/dvja.git'
        sh "mvn clean package"
      }
    }
    stage('Publish to S3') {
      steps {
        sh "aws s3 cp target/dvja-1.0-SNAPSHOT.war s3://ako2020-2-buildartifacts-1gz6t0lx1r4zq/dvja-1.0-SNAPSHOT.war"
      }
    }
    stage('Tidy up') {
      steps {
        cleanWs()
      }
    }
  }
}
