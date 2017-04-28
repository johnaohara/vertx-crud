node("launchpad-maven") {
  checkout scm
  stage("Deploy database") {
    sh "oc new-app -p POSTGRESQL_USER=luke -p POSTGRESQL_PASSWORD=secret -p POSTGRESQL_DATABASE=my_data -p DATABASE_SERVICE_NAME=my-database --name=my-database --docker-image=registry.access.redhat.com/openshift3/postgresql-92-rhel7:latest"
  }
  stage("Build") {
    sh "mvn fabric8:deploy -Popenshift -DskipTests"
  }
  stage("Deploy")
}
