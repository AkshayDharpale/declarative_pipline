pipeline {
    agent none

    stages {

        stage('Non-Parallel') {
           agent{
                   label "Windows_Node"
                   }
            steps {
                echo 'This will execute first' 
            }
        }

        stage('Run Tests') {
           parallel{
              stage('Test on Windows') {
                    agent{
                        label "Windows_Node"
                     }
                     steps {
                         echo 'Task 1 on agent' 
                        }
                }
              stage('Test on Linux') {
                    agent{
                        label "Linux_Node"
                     }
                     steps {
                         echo 'task 2 on agent' 
                        }
                }
           }
        }

    }

 post {
     always{
         echo "This will always run"
     }
     success{
         echo "This will run only if successfull"
     }
     failure{
         echo "This will run only if failure!!"
     }
     unstable{
         echo "This will run only if the run marked as unstable!!"
     }
     changed{
         echo "This will run only if the state of the pipeline changed"
         echo "For example, the pipeline is previously failing but is now successfull "
     }
 }
 
}
