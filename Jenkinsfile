node{
def mavenHome=tool name:"maven3.8.4"
echo "The node name is :${env.NODE_NAME}"
echo "The Job name is : ${env.JOB_NAME}"
echo "The Build number is : ${env.BUILD_NUMBER}"

stage('CheckoutCode'){
git branch: 'development', credentialsId: 'f14ae53c-aebe-47f3-b3a7-35af843a9a92', url: 'https://github.com/Shaziya007/maven-web-app.git'
}//checkout code
stage('Build'){
sh "$mavenHome/bin/mvn clean package"
}//build  close
stage('DeployAppIntoTomcat'){
sshagent(['0319cc43-91bc-4cbf-903f-b3aebed0320d']) {
sh "scp -0 StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.93.15.193:/opt/apache-tomcat-9.0.94/webapps"
    // some block
}
}
}//node closing

