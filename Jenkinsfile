pipeline {
  agent any
  stages {
    //stage('build start') {
    //  steps {
    //    slackSend(message: "Build ${env.BUILD_NUMBER} Started", color: 'good', tokenCredentialId: 'slack-key')
    //  }
    //}      
    stage('git pull') {
        steps {
            // https://github.com/IaC-Source/GitOps.git will replace by sed command before RUN
            git url: 'https://github.com/leechistest/GitOps.git', branch: 'main'
        }
    }
    stage('k8s deploy'){
        steps {
            kubernetesDeploy(kubeconfigId: 'kubeconfig',
                 configs: '*.yaml')
        }
    }
    
    //stage('send diff') {
    //    steps {
    //    script {
    //      def publisher = LastChanges.getLastChangesPublisher "PREVIOUS_REVISION", "SIDE", "LINE", true, true, "", "", "", "", ""
    //      publisher.publishLastChanges()
    //      def htmlDiff = publisher.getHtmlDiff()
    //      writeFile file: "build-diff-${env.BUILD_NUMBER}.html", text: htmlDiff
    //    }	
    //    slackSend(message: """${env.JOB_NAME} #${env.BUILD_NUMBER} End
    //    (<${env.BUILD_URL}/last-changes|Check Last changed>)
    //    """, color: 'good', tokenCredentialId: 'slack-key')             
    //    }
    //}
    
  }
}
