pipeline {
  agent any
  stages {
    stage("Git Checkout"){
           steps{
               git branch: 'main', url: 'https://github.com/Yogesh238/kupos_python_source.git'
              }
    }
    stage('Install Flask Package') {
      steps {
        sh 'pip install -r requirements.txt'
      }
    }
    stage('run') {
      steps {
        sh 'python app.py &'
      }   
    }
  }
}
