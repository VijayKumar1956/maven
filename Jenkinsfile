node('master') {

    stage('ContinuousDownload') {
        
        git 'https://github.com/VijayKumar1956/maven.git'
    
    }
    stage('ContinuousBuild') {
    
    sh '''mvn clean'''
    sh '''mvn package'''
    
    }    
    stage('ContinuousDepolyment') {
        
    sh 'scp -pr  /var/jenkins_home/workspace/NewMaven_master-LTXOB7WBJPSGU6Q7KEV2Y6NGYAMHUU7KENXHGBA2D6K6YMA7B4WA/webapp/target/webapp.war vagrant@10.10.10.22:/var/lib/tomcat7/webapps/qaenv.war'
        
    }
    stage('ContinuousTesting') {
    
    git 'https://github.com/VijayKumar1956/TestingOnLinux.git'
    sh 'java -jar /var/lib/jenkins/workspace/CodeAsPipelineFromGit/testing.jar'
    
    }
    stage('ContinuousDelivery') {
        
   
    sh 'scp -pr /var/jenkins_home/workspace/NewMaven_master-LTXOB7WBJPSGU6Q7KEV2Y6NGYAMHUU7KENXHGBA2D6K6YMA7B4WA/webapp/target/webapp.war  vagrant@10.10.10.23:/var/lib/tomcat7/webapps/prodenv.war'
    
    }

    

}

