node('master') {

    stage('ContinuousDownload') {
        
        git 'https://github.com/VijayKumar1956/maven.git'
    
    }
    stage('ContinuousBuild') {
    
    sh '''mvn clean mvn package'''
    
    }    
    stage('ContinuousDepolyment') {
        
    sh 'scp -pr /var/lib/jenkins/workspace/CodeAsPipeline/webapp/target/webapp.war  vagrant@10.10.10.22:/var/lib/tomcat7/webapps/qaenv.war'
        
    }
    stage('ContinuousTesting') {
    
    git 'https://github.com/VijayKumar1956/TestingOnLinux.git'
    sh 'java -jar /var/lib/jenkins/workspace/CodeAsPipeline/testing.jar'
    
    }
    stage('ContinuousDelivery') {
        
    input message: 'Please confirm to deploy the artifact into Production', submitter: 'jaggu,vinny'
    sh 'scp -pr /var/lib/jenkins/workspace/CodeAsPipeline/webapp/target/webapp.war  vagrant@10.10.10.23:/var/lib/tomcat7/webapps/prodenv.war'
    
    }

    

}

