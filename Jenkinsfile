#!groovy

node{
    stage ('checkout'){
        git branch: 'master', credentialsId: 'b7ab409b-a46f-46d6-9c2b-070bf68ed106', url: ' https://github.com/jenkinsexamples/mavenweb.git'
    }
    
    stage ('package'){
        sh 'mvn clean package'
    }
    stage ('tomcat'){
        sh 'cp $WORKSPACE/target/*.war /home/jenkins/tomcat/webapps'
    }
    stage ('sonarqube'){
        sh 'mvn sonar:sonar'
    }
    stage ('nexus'){
        sh 'mvn deploy'
    }
}
}
