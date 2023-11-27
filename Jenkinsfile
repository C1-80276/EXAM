pipeline {
    agent any

    stages {
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_PaLl5Fxzkq8et76Hg8CaWv9__SQ | /usr/local/bin/docker login -u chiraag77 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/local/bin/docker build -t chiraag77/resume_web:1 .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/local/bin/docker image push chiraag77/resume_web:1'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/local/bin/docker service rm exam3'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/local/bin/docker service create --name exam3 --replicas 5 -p 9876:80 chiraag77/resume_web:1'
            }
        }
    }
}

