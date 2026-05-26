node{

def mavenHome = tool name: 'maven3.9.14'

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])



stage('CheckOutCode'){
git branch: 'development', credentialsId: 'ce4dfd58-070c-4358-aea3-836f057d9165', url: 'https://github.com/MithunTechnologiesDevOps/Maven-Web-Application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcatServer'){
sshagent(['0a8d3a81-6f62-475b-8b2f-4c450e27eb68']) {
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.42.155:/opt/apache-tomcat-9.0.117/webapps/"
}
}
*/
}
