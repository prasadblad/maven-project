pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project.git'
        }
    }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MyMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'MyMaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'MyMaven') {
                    sh 'mvn install'
                }
            }
        }

        stage ('build && SonarQube analysis') {
            steps {
		withSonarQubeEnv('sonar') {
                    withMaven(maven : 'MyMaven') {
                        sh 'mvn clean package sonar:sonar'
                    }
		}	
            }
        }
}
}
