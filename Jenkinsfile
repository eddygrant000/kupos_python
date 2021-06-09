pipeline {
  agent any
  stages {
    stage("Git Checkout"){
           steps{
               git branch: 'main', url: 'https://github.com/Yogesh238/kupos_python_source.git'
              }
    }
    stage('Build and Deploy') {
      steps {
        sshagent(credentials : ['appserver']) {
        sh 'ssh -o StrictHostKeyChecking=no root@54.84.99.76 apt update'
        sh 'ssh -o StrictHostKeyChecking=no root@54.84.99.76 apt install python3-pip'
        sh 'ssh -o StrictHostKeyChecking=no root@54.84.99.76 systemctl stop flask.service'
        sh 'scp -r * root@54.84.99.76:/root/flaskapp'
        sh 'ssh -o StrictHostKeyChecking=no root@54.84.99.76 pip3 install -r /root/flaskapp/requirements.txt'
        sh 'ssh -o StrictHostKeyChecking=no root@54.84.99.76 systemctl start flask.service'
      }
    }
    }
  }
}
