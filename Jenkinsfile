pipeline {

    agent {
        label 'jenkins-jenkins-agent'
    }

    options {
        disableConcurrentBuilds()
        quietPeriod(0)
    }

    stages {
        stage("TESTING") {
            steps {
                script {

                    dir('ansible-automation/inventory') {

                        def files = findFiles()

                        files.each { file ->

                            def clusterName = file.name.take(file.name.lastIndexOf('.'))

                            def CREDENTIAL_ID = "OC_" + clusterName.toUpperCase();

                            withCredentials([string(credentialsId: CREDENTIAL_ID, variable: 'OC_TOKEN'),
                                             string(credentialsId: "OC_API_HOST", variable: 'OC_API_HOST')]) {
                                sh """
                                   oc login  --token=${OC_TOKEN} --server=${OC_API_HOST}
                                   oc start-build nginx-site-bigbuckracing-com-build -n site-bigbuckracing-com -F
                                   oc rollout restart statefulset/site-bigbuckracing-com-ngnix -n site-bigbuckracing-com
                                """
                            }
                        }
                    }
                }
            }
        }

    }
}
