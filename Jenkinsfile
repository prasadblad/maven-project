pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prasadblad/maven-project.git'
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
        
        stage('deploy to tomcat'){
            steps {
	            sshagent(['1a502a02-2fb7-42dd-bf3a-5bacfc59e3c0']) {
	                sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@18.188.201.192:/var/lib/tomcat'
}
}
}
