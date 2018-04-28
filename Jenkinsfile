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
    
            sh "docker build -t registry.cn-hangzhou.aliyuncs.com/spacexnice/jenkins-slaves-java8:latest ."
          }
        }
      }

      stage 'Build and push images!'
        container('docker') {
            stage 'build'
      }
    }
  }