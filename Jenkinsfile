pipeline {
    agent any

    stages {
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_PaLl5Fxzkq8et76Hg8CaWv9__SQ | docker login -u chiraag77 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh 'docker build -t chiraag77/resume_web:1 .'
            }
        }
        stage ('docker push image') {
            steps {
                sh 'docker image push chiraag77/resume_web:1'
            }
        }
        stage ('docker remove service') {
            steps {
                sh 'docker service rm exam3'
            }
        }
        stage ('docker create service') {
            steps {
                sh 'docker service create --name -d exam3 --replicas 5 -p 9876:80 chiraag77/resume_web:1'
            }
        }
    }
}

