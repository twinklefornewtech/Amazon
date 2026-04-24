pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                echo "Cloning the code"
                git branch:"master",url:"https://github.com/twinklefornewtech/Amazon.git"
            }
        }
        stage('Build for Amazon'){
            steps{
                dir('Amazon'){
                    echo "Generating Build for Amazon..."
                    sh "mvn clean install"
                }
            }
        }
    }
    post{
        success{
            dir('Amazon/Amazon-Web/target'){
                echo "Deploying to tomcat..."
                sh 'curl -u admin:admin123 -T Amazon.war "http://localhost:8081/manager/text/deploy?path=/hookapp&update=true"'
            }
        }
        failure{
            echo "Amazon Build failed"
        }
    }
}
