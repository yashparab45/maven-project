pipeline {
 agent {
  label 'SERVER 1'
}
tools {
  maven 'mymaven'
}
stages {
  stage('build') {
    steps {
     sh 'mvn clean package'
    }

    post {
      success {
       archiveArtifacts artifacts: '/home/ubuntu/jenkins/workspace/CICD/server/target
/*.war' 
      }
    }
  }
 }
}


















