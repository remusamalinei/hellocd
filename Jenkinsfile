pipeline {
    agent {
        kubernetes {
            yaml '''
              apiVersion: v1
              kind: Pod
              spec:
                containers:
                  - name: alpine
                    image: alpine:3.18.2
                    command: ["sh", "-c", "sleep 30"]
            '''
        }
    }
    stages {
        stage("Run alpine") {
            steps {
                container("alpine") {
                    sh "date"
                }
            }
        }
        stage("Print folder name") {
            steps {
                withFolderProperties {
                    echo "${env.folder_name}"
                }
            }
        }
    }
}