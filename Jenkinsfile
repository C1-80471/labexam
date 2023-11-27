pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80471/labexam.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_qadgYsLNo981IzgC1s4EtZpBdHY | /usr/bin/docker login -u pravin1015 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t pravin1015/labexam .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push pravin1015/labexam'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm labexam'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9876:80 --replicas 5 pravin1015/labexam'
            }
        }
    }
}
