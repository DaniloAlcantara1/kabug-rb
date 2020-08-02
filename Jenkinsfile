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
                sh 'rm -f Gemfile.lock'
                sh 'bundle install'
            }
        }
        stage('Test'){
            steps{
                echo 'Running Regression Tests'
                sh 'bundle exec cucumber -p ci'
                cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', jsonReportDirectory: 'logs', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
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