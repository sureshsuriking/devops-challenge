pipeline {
    agent any
     environment {
        def name = "my name"
        def pwdv = "suresh"
        def branch="main"
    }
    parameters {
        string(name: 'STRING_VARIABLE', defaultValue: 'TestTrainer', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
                 git branch: "${branch}", url: 'https://github.com/Arvind9719/hello-world.git'
                 dir('MOVE') {
                    sh ("touch test.txt")
                    sh ("cat test")
                    readFile 'test'
                }
            }
        }
         stage('Gmkdir') {
            steps {
                sh "mkdir -p abc/ghi/xyz"
                // timeout(time: 10, unit: 'SECONDS') {
                //     sleep 20
                // }
            }
        } 
        stage('Hi') {
            steps {
                dir('abc') {
                    dir('ghi') {
                        dir('xyz') {
                            sh("touch fffffff.txt")
                        }
                    }
                }
                dir('abc/ghi/xyz') {
                   sh("touch ttttttttttt.txt")
                }
                echo 'Hello World'
                dir('abc/ghi') {
                  deleteDir()
                }
                timestamps {
                    echo "asdasd"
                }
            }
        }
         stage('Variable Initialization') {
            steps {
                script {
                    sh("echo ${name}")
                    writeFile file: 'test-write-file', text: 'asdasdasdasdasd'
                }
            }
        }
        stage('Validate') {
            // when { branch 'master' }	
            steps {
                script {
                    if("${STRING_VARIABLE}" == "TestTrainer") {
                        error 'Triggered error'
                    } else {
                        echo "The input was different from TestTrainer so proceeding"
                    }
                     if("${CHOICE}" == "Three") {
                        error 'Triggered error'
                    } else {
                        echo "The input was different from TestTrainer so proceeding"
                    }
                }
            }
        }
         stage('Confirm button') {
            steps {
                input 'Please confirm'
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '3c1b6eec-6ada-407b-8b69-dc3f27bc9bf6', url: 'https://gitlab.com/suresh61deepu/git.git']]])
                withCredentials([string(credentialsId: 'aws', variable: 'SECRET_TEXT')]) {
                sh("echo $SECRET_TEXT")
                }
               
                sh("echo asdasdasd")
            }
        }
       
        stage('Loop') {
            steps {
                echo 'Hello World'

                script {
                    def browsers = ['chrome', 'firefox']
                    for (int i = 0; i < browsers.size(); ++i) {
                        echo "Testing the ${browsers[i]} browser"
                    }
                }
            }
        }
         stage('Parallel Stage') {
            // when { branch 'master' }
            failFast true
            parallel {
                stage('Branch A') {
                    steps {
                        echo " Branch A"
                    }
                }
                stage('Branch B') {
                    steps {
                        echo "On Branch B"
                    }
                }
		    }
	    }
	    
    }

