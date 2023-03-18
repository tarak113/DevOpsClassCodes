
pipeline {
    agent any
    tools{
        maven 'mymaven'
    }

    stages {
        stage('cloningRepo') {
            steps {
                echo 'This is stage 1'
                git 'https://github.com/NikitasGithub/DevOpsClassCodes.git'
            }
        }
        stage('Compile') {
            steps {
                echo 'This is stage 2'
                bat 'mvn compile'
            }
        }
        
        stage('Code Review') {
            steps {
                echo 'This is stage 3'
                bat 'mvn pmd:pmd'
            }
            post{
                success{
                    recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
                }
            }
        }
        
        stage('Test') {
            steps {
                echo 'This is stage 4'
                bat 'mvn test'
            }
        }
        
        stage('packaging my code') {
            steps {
                echo 'This is stage 5'
                bat 'mvn package'
            }
        } 
        
    }
}
