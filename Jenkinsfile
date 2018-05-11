node('master') {

    stage('ContinuousDownload') {
        
        git 'https://github.com/VijayKumar1956/maven.git'
    
    }
    stage('ContinuousBuild') {
    
    sh '''mvn clean'''
    sh '''mvn package'''
    sh 'chmod 777 /var/jenkins_home/workspace/maven_master-CAUIYSUDU6ZFDVGYGIP7VKJC3KN5HUV5PRMYL7EAJJNZ7BAF4A7A/webapp/target/webapp.war'
    
    }    
    stage('ContinuousDepolyment') {
        
    sh 'scp -pr  /var/jenkins_home/workspace/maven_master-CAUIYSUDU6ZFDVGYGIP7VKJC3KN5HUV5PRMYL7EAJJNZ7BAF4A7A/webapp/target/webapp.war vagrant@10.10.10.22:/var/lib/tomcat7/webapps/qaenv.war'
        
    }
    stage('ContinuousTesting') {
    
    git 'https://github.com/VijayKumar1956/TestingOnLinux.git'
    sh 'java -jar /var/lib/jenkins/workspace/CodeAsPipelineFromGit/testing.jar'
    
    }
    stage('ContinuousDelivery') {
        
   
    sh 'scp -pr /var/jenkins_home/workspace/maven_master-CAUIYSUDU6ZFDVGYGIP7VKJC3KN5HUV5PRMYL7EAJJNZ7BAF4A7A/webapp/target/webapp.war  vagrant@10.10.10.23:/var/lib/tomcat7/webapps/prodenv.war'
    
    }

    

}

