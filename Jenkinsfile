pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }
    stage ('Build') {
      steps{
      sh 'mvn clean package'
      }
    }
    stage ('Deploy-To-Tomcat') {
            steps {
            sshagent(['Tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war kali@192.168.1.81:/home/kali/Downloads/apache-tomcat-9.0.63/webapps/webapp.war'
             }     
           }       
    }
  }
}
