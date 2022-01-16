pipeline {
    agent {
      label 'jenkins-agent-01'
    }
    stages {
        stage('Git') {
             steps {
                 git branch: 'Molecule', changelog: false, poll: false, url: 'https://github.com/GrigoriyAzatyan/kibana-role.git'
             }
        }
        stage('Install requirements') {
             steps {
                 sh 'pip3 install -r /opt/jenkins_agent/workspace/Declarative/test-requirements.txt'
                 sh 'ansible-galaxy install -p . git+https://github.com/GrigoriyAzatyan/kibana-role.git --force'
             }
        }
        stage('Start molecule') {
             steps {
                  sh 'molecule test --destroy=never'
             }
        }
    }
}
