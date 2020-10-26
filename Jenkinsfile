pipeline {
    agent {
        docker {
            image 'itinha/rubywd'
        }
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building or Resolve Dependencies'       
                sh 'bundle install'
            }
        }
        stage('Test') {
            steps {
                echo 'Runing regression tests'
                sh 'bundle exec cucumber -p ci'
            }
                
        }
    
        stage('UAT') {
            steps {
                echo 'Wait for User Acceptance'
                input(message: 'Go to production?', ok: 'Yes')
            }
        }
        stage('Prod') {
            steps {
                echo 'WebApp is Ready'
            }
        }
    }
}