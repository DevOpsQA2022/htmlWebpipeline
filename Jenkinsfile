pipeline {
    agent any
    tools{
        maven 'local_maven'
    }

    stages {
        stage('Build') {
            steps {
               sh 'mvn clean package'
            }
            post{
                 success{
                     echo"Archiving the Artifacts"  
                     archiveArtifacts artifacts: '**/target/*.war'
                 }
                 }
            }
        }
                
           
      stages {
        stage('Deloy') {
            steps {
                deploy adapters: [tomcat8(credentialsId: 'a113e3b9-6ba1-471a-8989-c99776136ead', path: '', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
                echo 'successfully'
            }
        }
      
    }
}
