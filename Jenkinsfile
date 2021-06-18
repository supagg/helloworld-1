pipeline {
    agent any
    environment {
        webapps=C:\apache-tomcat-9.0.46-windows-x64\apache-tomcat-9.0.46\webapps
    }
    tools { 
        maven 'Maven' 
        jdk 'Java_8' 
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
  
        stage ('Initialize') {
            steps {
                    echo "PATH = $PATH"
                    echo "M2_HOME = $M2_HOME"
            }
        }
        stage ('GIT Checkout') {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                userRemoteConfigs: [[url: 'https://github.com/supagg/helloworld-1.git']]])
            }
        }
        stage ('Build code') {
            steps{
                bat 'mvn clean install'
            }
        }   
        stage ('Deploy code'){
            steps{
                bat 'IF EXIST %webapps%\helloworld-1.1.jar DEL /F %webapps%\helloworld-1.1.jar
                     copy target\helloworld-1.1.jar %webapps%\helloworld-1.1.jar'
            }
        }
    }

}
