pipeline {
 agent {
  label 'SERVER 1'
}
tools {
  maven 'maven'
}
stages{
  stage('build') {
    steps {
     sh 'mvn clean package'
    }

    post {
      success {
       archiveArtifacts artifacts: '**/target/*.war' 
      }
    }
  }
 }
}


















