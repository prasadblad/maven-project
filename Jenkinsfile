pipeline {
    agent any
 
    stages {
stage('scm checkout'){
steps{
git 'https://github.com/prasadblad/maven-project.git'
}
}
stage('compile source code'){
steps{
withMaven (maven: 'MyMaven'){
sh 'mvn compile'}
}
}
stage('test'){
steps{
withMaven(maven : 'MyMaven') {
sh 'mvn test'
}
}
}
 
stage('build and sonar analysis'){
steps{
withSonarQubeEnv('sonar') {
   withMaven(maven : 'MyMaven') {
sh 'mvn clean package sonar:sonar'
}
}
}
}
}
       
    }
