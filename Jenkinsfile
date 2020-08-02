pipeline{
    agent any
    
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
                sh 'bundle exec cucumber'
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