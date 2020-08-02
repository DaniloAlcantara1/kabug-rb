pipeline{
    agent {
        docker{
            image 'qaninja/rubywd'
        }
    }
    
    stages{
        stage('Build'){
            steps(){
                echo 'Building or resolve Dependencies!'
                sh 'bundle install'
            }
        }
        stage('Test'){
            steps{
                echo 'Running Regression Tests'
                sh 'rm -f Gemfile.lock'
                sh 'bundle exec cucumber -p ci'
            }
        }
        stage('UAT'){
            steps{
                echo 'Wait for User Aceptance'
                input(message: 'Go tp production?', ok: 'yes')
            }
        }
        stage('Prod'){
            steps{
                echo 'App is Ready =)'
            }
        }
    }
    
    
}