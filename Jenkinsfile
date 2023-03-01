pipeline {
	agent any
	stages {
		stage ("creating cutomworkspace") {
                steps {
		customWorkspace '/mnt/23Q1'
	}
	}
       stages {
		stage ('install docker') {
			steps {
			sh 'yum install docker -y ; systemctl start docker'
			}
		}
		stage ('clone repository') {
			steps{
				checkout scm
			}
		}
		stage ('Deploy to 23Q1') {
			steps {
			sh 'git clone https://github.com/snehalshinde1996/project1.git -b 23Q1'
			sh 'chmod 777 /mnt/23Q1/project1/index.html'
			sh 'docker run -itdp 80:80 --name 23Q1 httpd'
			sh 'docker cp /mnt/23Q1/project1/index.html 23Q1:/usr/local/apache2/htdocs'
			}
		}

		stage ('Deploy to 23Q2') {
			steps {
			dir ('/mnt/23Q2') {
			sh 'rm -rf /mnt/23Q2/*'
			sh 'git clone https://github.com/snehalshinde1996/project1.git -b 23Q2'
			sh 'chmod 777 /mnt/23Q2/project1/index.html'
			sh 'docker run -itdp 81:80 --name 23Q2 httpd'
			sh 'docker cp /mnt/23Q2/project1/index.html 23Q2:/usr/local/apache2/htdocs'
			}
		}
		}
		stage ('Deploy to 23Q3') {
			steps {
			dir ('/mnt/23Q3') {
			sh 'rm -rf /mnt/23Q3/*'
			sh 'git clone https://github.com/snehalshinde1996/project1.git -b 23Q3'
			sh 'chmod 777 /mnt/23Q3/project1/index.html'
			sh 'docker run -itdp 82:80 --name 23Q3 httpd'
			sh 'docker cp /mnt/23Q3/project1/index.html 23Q3:/usr/local/apache2/htdocs'
			}
		}
		}
	}
}
