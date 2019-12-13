pipeline {
    agent any
    tools {
    maven 'Default'
  }
    stages {
         stage ('Build Servlet Project') {
            
            steps {
                /*For windows machine */
               //bat  'mvn clean package'

                /*For Mac & Linux machine */
             
                sh  'mvn clean package'
            }

            post{
                success{
                    echo 'Now Archiving ....'

                    archiveArtifacts artifacts : '**/*.war'
                }
            }
         stage ('deploy build in staging area'){
             steps {
                     build job : 'deploy_stagingarea_pipeline'
                }
             }    
    }
}
