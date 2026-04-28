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
        stage('Build for SKY'){
            steps{
                dir('SKY'){
                    echo "Generating Build for SKY..."
                    sh "mvn clean install"
                }
            }
        }
        stage('Build for SpringCore'){
            steps{
                dir('SpringCore'){
                    echo "Generating Build for SpringCore..."
                    sh "mvn clean install"
                }
            }
        }
        stage('Build for SpringDemo'){
            steps{
                dir('SpringDemo'){
                    echo "Generating Build for SpringDemo..."
                    sh "mvn clean install"
                }
            }
        }
         stage('Build for SpringNew'){
            steps{
                dir('SpringNew'){
                    echo "Generating Build for SpringNew..."
                    sh "mvn clean install"
                }
            }
        }
    }
    post{
        success{
            dir('Amazon/Amazon-Web/target'){
                echo "Deploying to tomcat..."
                sh 'curl -u admin:admin123 -T Amazon.war "http://localhost:8081/manager/text/deploy?path=/Amazon&update=true"'
            }
            dir('SKY/SKY-Web/target'){
                echo "Deploying to tomcat..."
                sh 'curl -u admin:admin123 -T SKY.war "http://localhost:8081/manager/text/deploy?path=/SKY&update=true"'
            }
            dir('SpringNew/Spring-Web/target'){
                echo "Deploying to tomcat..."
                sh 'curl -u admin:admin123 -T SpringNew.war "http://localhost:8081/manager/text/deploy?path=/SpringNew&update=true"'
            }
            dir('SpringCore/target'){
                echo "Generated jar for SpringCore..."
            }
            dir('SpringDemo/target'){
                echo "Generated jar for SpringDemo..."
            }
        }
        failure{
            echo "Any one Build failed"
        }
    }
}
