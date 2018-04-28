podTemplate(label: 'jenkins-slave-pod',
  containers: [
    containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true)
  ],volumes: [
     hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')
  ]){
    node ('jenkins-slave-pod') {

      stage('Get the jenkins-slave project') {

        checkout scm

        // git url: 'https://github.com/hjue/jenkins-slaves.git'
        
        container('docker') {
          stage('Build blog project') {
    
            sh "docker build -t registry-internal.cn-hangzhou.aliyuncs.com/gionee-projects/jenkins-slaves-java8:latest ."
          }
        }
      }

      stage('Build and push images!'){
        container('docker') {
            withDockerRegistry([credentialsId: '06897695-306c-4851-8585-a939473f1221', url: 'http://registry-internal.cn-hangzhou.aliyuncs.com']) {
                sh "docker push registry-internal.cn-hangzhou.aliyuncs.com/gionee-projects/jenkins-slaves-java8:latest"
            }
        }
      }

    }
  }