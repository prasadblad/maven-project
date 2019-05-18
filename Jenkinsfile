pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project'
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


//        stage ('install Stage') {
//            steps {
//                withMaven(maven : 'MyMaven') {
//                  sh 'mvn install'
//                }
//            }
//        }

//         stage ('deploy to tomcat') {
//             steps {
//                 sshagent(['f39cd834-5e32-428e-965f-d6020b95c133']) {
//                 sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.38.135:/var/lib/tomcat/webapps'
//      }
//             }
//   }
        
        stage ('sonar') {
                steps {
                   withSonarQubeEnv('sonar')
                    withMaven(maven : 'MyMaven') {
                        sh 'clean install sonar:sonar'
                    
                }
            }
        }
        
    }
}
