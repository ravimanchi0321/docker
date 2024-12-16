// pipeline {
//     agent any

//     stages {
//         stage('git checkout') {
//             steps {
//                 git branch: 'master', url: 'https://github.com/ravimanchi0321/docker.git'
//         }
//         }
//         stage('docker build') {
//             steps {
//                 sh 'docker build -t "$JOB_NAME":v1."$BUILD_ID" .'
//                 sh 'docker tag "$JOB_NAME":v1."$BUILD_ID" ravikumarmanchi/"$JOB_NAME":v1."$BUILD_ID"'
//                 sh 'docker tag "$JOB_NAME":v1."$BUILD_ID" ravikumarmanchi/"$JOB_NAME":latest'
//                 sh 'docker rmi k8s:v1."$BUILD_ID"'
//         }
//         }
//         stage('docker loging and push') {
//             steps {
//                 withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'pswd', usernameVariable: 'docker')]) {
//                 sh 'docker login -u="${docker}" -p="${pswd}"'
//             }
//         }
//         }
//         stage('docker push') {
//             steps {
//                 sh 'docker push ravikumarmanchi/"$JOB_NAME":v1."$BUILD_ID"'
//                 sh 'docker push ravikumarmanchi/"$JOB_NAME":latest'
//         }
//         }
//         stage('DEPLOYMENT ON EKS') {
//             steps {
//                 sh 'ansible-playbook playbooks/k8s.yaml'
                    
//             }            
//         }  
       
        
//     }
// }
pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/KBHASKAR306/Job-Portal-Website.git'
        }
        }
        stage('docker build') {
            steps {
                sh 'docker build -t "$JOB_NAME":v1."$BUILD_ID" .'
                sh 'docker tag "$JOB_NAME":v1."$BUILD_ID" ravikumarmanchi/"$JOB_NAME":v1."$BUILD_ID"'
                sh 'docker tag "$JOB_NAME":v1."$BUILD_ID" ravikumarmanchi/"$JOB_NAME":latest'
                sh 'docker rmi demo-jenkins:v1."$BUILD_ID"'
        }
        }
        stage('docker crate container') {
            steps {
               sh 'docker rm -f web'
               sh 'docker run -itd --name web -p 80:80 ravikumarmanchi/"$JOB_NAME":latest'
        }
        }    
      
    }
}
