pipeline {
    agent {
  label 'SERVER 1'
   }
   tools {
  maven 'mymaven'
  }

   stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        post {
  success {
     archieveArtifacts artifacts: '**/target/*.war'
}

    }
}

