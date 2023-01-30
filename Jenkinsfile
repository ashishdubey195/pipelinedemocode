pipeline{
    
    tools{
         // What tool version forbuild stages
         maven 'mymaven'
    }
    agent any
    
    stages{
        
        stage('clone Repo')
        {
           steps{
            echo 'This is stage 1'
            git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
        }
    
    }
           
           stage('compile')
           {
               steps{
               
               sh 'mvn compile'
           }
        }
              stage('codereview')
              {
                   steps{
               
               sh 'mvn pmd:pmd'
           }
        post{
            success{
                recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
            }
        }
    }
              stage('test')
        {
           steps{
               
               sh 'mvn test'
           }
        post{
            success{
                junit 'target/surefire-reports/*.xml'
            }
        }
        }
        stage('Package')
        {
            steps{
                sh 'mvn package'
            }
        }
        
       stage('Deploy')
        {
            steps{
                echo "Deploy the code"
            }
        }
    }
}

