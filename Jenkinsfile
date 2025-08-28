pipeline{
    agent any
    stages{
        stage('Github Checkout'){
          steps{
                 git branch: 'main',
                url:'https://github.com/Sapna35/addressbook-cicd-sapna'
          }
        }
        stage('compiling the code'){
          steps{
                 sh 'mvn compile'
          }
        }
        stage('Run Tests'){
            steps{
                sh 'mvn test'
            }
        }
        stage('QA'){
            steps{
                sh 'mvn pmd:pmd'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage("deploy the project on tomcat"){
            steps{
                sh "sudo mv ${WORKSPACE}/target/addressbook.war /home/ubuntu/apache-tomcat-8.5.100/webapps/"
            }
        }
    }
}
