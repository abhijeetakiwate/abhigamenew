pipeline {
  agent{
    label{
      label "qa"
 customWorkspace "/mnt/pipeline1" 
    }
  }
  stages {
    stage ("deploy to container1") {
      steps {
        
        sh "sudo docker volume create my-volume-1"
        sh "sudo cp /mnt/pipeline1/index.html /var/lib/docker/volumes/my-volume-1/_data"
        sh "chmod -R 777 /mnt/pipeline1/index.html"
        sh "chmod -R 777 /var/lib/docker/volumes/my-volume-1/_data"
        sh "sudo docker run -itdp 8084:80 -v my-volume-1:/usr/local/apache2/htdocs --name container-slave httpd"
  
      }
    }
  }
}
