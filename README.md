# Jenkins

## INFO

Exploring Jenkins.

## Start Local Environment

```shell
touch jenkins_home
```

```shell
docker build -t jenkins_custom .
```

```shell
docker compose up -d
```

## Setup Jenkins

### Plugins

- SonarQube Scanner for Jenkins
- Nexus Artifact Uploader
- Default Plugins

### Tools (Manage Jenkins -> Tools, (for binary))
- SonarQube Scanner installations
- JDK installations

### System (Manage Jenkins -> System, (for environment))
- SonarQube Servers (name: `sonarserver`, URL: `http://sonarqube:9000`, add `token`)

### Credentials

Nexus:
- System -> Global Credentials -> Add -> Kind: `Username with password`, ID: `nexuslogin`

Sonar:
- You should already have ID: `sonarserver`

## Setup SonarQube

### Token

Token is needed for Jenkins to upload analysis to sonarQube

Admin Account -> Security -> Generate Token

### Webhook

Webhook will send quality gate result back to Jenkins

Administration -> Configuration -> Webhooks
- URL: `http://jenkins_instance:8080/sonarqube-webhook/` (/sonarqube-webhook/ has been created by sonarqube plugin)

### Setup Nexus

## Backup

```shell
docker-compose down
```

More coming soon.

## Useful Links

[Built-in ENV Vars](https://www.jenkins.io/doc/book/pipeline/jenkinsfile/#using-environment-variables)
