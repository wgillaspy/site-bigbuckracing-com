pipeline {

    agent {
        label 'jenkins-jenkins-agent'
    }

    triggers {
        cron('H/15 * * * *')
    }

    options {
        disableConcurrentBuilds()
        quietPeriod(0)
    }

    stages {
        stage("TESTING") {
            steps {
                script {
                    withCredentials([string(credentialsId: "OC_LOCAL", variable: 'OC_TOKEN'),
                                     string(credentialsId: "OC_API_HOST", variable: 'OC_API_HOST')]) {
                        sh """ 
                           oc login  --token=${OC_TOKEN} --server=${OC_API_HOST} --insecure-skip-tls-verify
                           oc start-build nginx-site-bigbuckracing-com-build -n site-bigbuckracing-com -F
                           oc rollout restart statefulset/site-bigbuckracing-com-ngnix -n site-bigbuckracing-com
                        """
                    }
                }
            }
        }

    }
}
