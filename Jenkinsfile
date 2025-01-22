 pipeline {
  agent any
  environment {
      DOCKER_CREDENTIALS = credentials('923804f2-8e18-4e1f-82a8-420a5b9ed31b') // Use the ID of your credentials
  }
     stages {
         stage('Lint') {
             steps {
                 sh '''
                 #!/bin/bash
                 python3 -m venv venv
                 . ./venv/bin/activate
                 pip install flake8
                 flake8 app.py
                 '''
              }
         }
         stage('Format') {
             steps {
                 sh '''
                 #!/bin/bash
                 python3 -m venv venv
                 . ./venv/bin/activate
                 pip install black
                 black --check app.py
                 '''
             }
         }
         stage('Build') {
             steps {
                 sh 'echo $DOCKER_CREDENTIALS_PSW | docker login -u $DOCKER_CREDENTIALS_USR --password-stdin'
             }
         }
     }
 }
