pipeline {
    agent any

     triggers {
        //githubPush()
        cron('H/2 * * * *')
    }

    tools {
        maven 'Maven 3.9.6' // Name der Maven-Installation in der Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                // Code aus dem Versionskontrollsystem abrufen
                //git 'https://github.com/nima3608/hello-world.git'
                 git branch: 'main', url: 'https://github.com/nima3608/jenkinss.git' 
            }
        }

        stage('Build') {
            steps {
                // Kompilieren und Testen des Projekts
                script {
                    def mvnHome = tool name: 'Maven 3.9.6', type: 'maven'
                    env.PATH = "${mvnHome}/bin:${env.PATH}"
                }
                bat 'mvn clean compile'
            }
        }

        stage('Execute') {
            steps {
                // Ausführen des Java-Programms
                bat 'mvn exec:java -Dexec.mainClass="com.example.App"'
            }
        }
    }
}
