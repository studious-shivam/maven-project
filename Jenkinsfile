
pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git branch: 'master', url: 'https://github.com/studious-shivam/maven-project.git'
      }
    }

    stage('package the job') //validate then compile
    {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn clean package'
        }
      }
    }
    stage('deploy to tomcat server'){
      steps{sshagent(['tomcat-deployment']){
        sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ubuntu@13.201.185.162:/tmp/'
        //sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.20.221:/usr/share/tomcat/webapps'
      }
      }
    }
  }
}
