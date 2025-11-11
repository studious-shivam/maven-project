pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git branch: 'master', url: 'https://github.com/kumargaurav039/maven-project.git'
      }
    }
  }
}
