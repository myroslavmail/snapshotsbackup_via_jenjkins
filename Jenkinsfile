pipeline {
    agent {
        docker {
            image 'busybox'
        }
    }
    
    options{
        buildDiscarder(
            logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '77', numToKeepStr: '')
        )
    }
    
    triggers {
        cron('H H/6 * * *')
    }
    
    parameters {
            string (defaultValue: '180', description: 'days parameter', name: 'days', trim: false)
            string (defaultValue: 'name', description: 'volume tags', name: 'tags', trim: false)
    }
   
    stages {
        stage('Example') {
            steps {
                sh "./myscript.sh -d ${params.days} -t ${params.tags}"
            }
        }
    }
}
