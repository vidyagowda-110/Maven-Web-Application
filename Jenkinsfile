node {
def mavenHome = tool name: 'maven3.9.16'
stage('checkoutcode'){
git branch: 'development', credentialsId: '9d3d18e3-e672-4a31-9c2b-abaee9ae9f60', url: 'https://github.com/vidyagowda-110/Maven-Web-Application.git'
}
stage('build'){
sh "${mavenHome}/bin/mvn clean package"
}
stage('executesonarreport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('uploadartfactbynexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('deployappliintothetomcat'){
sshagent(['b0d52f8a-057f-4766-8532-5640debec25d']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.34.132:/opt/apache-tomcat-9.0.119/webapps"
    
}
}
}
