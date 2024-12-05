node {

echo "The Job name is: ${env.JOB_NAME}"
echo "The Node name is: ${env.NODE_NAME}"
echo "The Build number is: ${env.BUILD_NUMBER}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    
def mavenHome = tool name: 'maven3.9.8', type: 'maven'

stage('CheckOutCode') {
git branch: 'development', credentialsId: '354970ca-fa0d-4af3-8d2e-6756a0fa35a0', url: 'https://github.com/mithun-mss-sep-2024/maven-web-application.git'
}

stage('Build') {
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage('ExecuteSonarQubeReport') {
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactsIntoNexus') {
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcatServer') {
    
sshagent(['2de28b0a-e092-41bd-894b-f1d2047982ad']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.30.237:/opt/tomcat9/webapps/"
}
}
*/

}
