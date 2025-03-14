pipeline {
  agent {
       label 'maven'
   }
stages {
  stage('git_checkout') {
    steps {
      git branch: 'main', url: 'https://github.com/Raveendra-hm/java-example-artisantek.git'  
    }
  }

  stage('test_stage') {
    steps {
      echo "this is just for testing purpose !! !"
    }
  }

  stage('build_stage') {
    steps {
      sh 'mvn clean package'
    }
  }

  stage('deploy_stage') {
    steps {
      sh 'sudo cp target/*.war /opt/tomcat/apache-tomcat-9.0.68/webapps/'
    }
  }

 }
}

