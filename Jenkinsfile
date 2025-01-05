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
     sh 'mvn clean package' // One or more steps need to be included within the steps block.
    }

    post {
      success {
       archieveArtifacts artifacts: '**/target/*.war' // One or more steps need to be included within each condition's block.
      }
    }
  }

}
}


















