pipeline {
    agent any
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
    }

}
