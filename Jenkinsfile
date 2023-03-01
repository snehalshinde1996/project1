pipeline {
	agent {
		label 'built-in'
		customWorkspace '/mnt/23Q1'
	}

	stages {
		stage ('install docker') {
			steps {
			sh 'yum install docker -y ; systemctl start docker'
			}
		}
		stage ('Deploy to 23Q1') {
			steps {
			sh 'git clone <gitrepo> -b 23Q1'
			sh 'chmod 777 /mnt/23Q1/'
			}
		}

	}
}
