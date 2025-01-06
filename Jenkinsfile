pipeline {
 agent {
  label 'SERVER 1'
}

parameters {
  string defaultValue: 'Parab', name: 'LASTNAME'
}

environment {
  NAME = "Yash"
}
tools {
  maven 'maven'
}
stages{
  stage('build') {
    steps {
     sh 'mvn clean package'
     echo "Hello $NAME ${params.LASTNAME}"
    }

    post {
      success {
       archiveArtifacts artifacts: '**/target/*.war' 
      }
    }
  }
 }
}


















