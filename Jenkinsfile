pipeline 
{
 agent {
  label 'SERVER 1'
}
tools {
  maven 'maven'
}
stages
 {
  stage('build')
   {
    steps {
     sh '-B -DskipTests clean package'
    }

  }
}

}


















