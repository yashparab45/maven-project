pipeline {
 agent {
  label 'SERVER 1'
}

parameters {
    choice choices: ['DEV', 'PROD'], name: 'select_environments'
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
      script{
                file = load "script.groovy"
                file.hello()
            }
     sh 'mvn clean package -DskipTests=true'
     
    }
 }

    stage('test') {
      parallel {
        stage('testA') {
          agent {label 'SERVER 1'}
          steps {
            sh 'mvn test'
          }
        }
        stage('testB') {
           agent {label 'SERVER 1'}
          steps {
            sh 'mvn test'
          }
        }
       }

       post {
      success {
        dir("webapp/target") {
       stash name: "maven-build" , includes: "*.war"
      }
    }
    }
 }

    stage('deploy_dev') {
        when { expression {params.select_environments == 'DEV'}
        beforeAgent true}
        agent { label 'SERVER 1' }
        steps
        {
            dir("/var/www/html")
            {
                unstash "maven-build"
            }
            sh """
            cd /var/www/html/
            /usr/lib/jvm/java-8-openjdk-amd64/bin/jar" -xvf webapp.war
            """
        }
    
    }

     stage('deploy_prod')
    {
      when { expression {params.select_environments == 'PROD'}
        beforeAgent true}
        agent { label 'SERVER 2' }
        steps
        {
             timeout(time:5, unit:'DAYS'){
                input message: 'Deployment approved?'
             }
            dir("/var/www/html")
            {
                unstash "maven-build"
            }
               sh """
               cd /var/www/html/
               /usr/lib/jvm/java-8-openjdk-amd64/bin/jar" -xvf webapp.war
               """

}
}
}
}


















