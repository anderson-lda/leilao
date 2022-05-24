# leilao
Projeto simples em Java para treinamento de Jenkins.

# Instalação
Foi baixado no site do Jenkins o arquivo .war e, dentro da pasta ao qual ele se encontra, é rodado o seguinte comando:
java -jar jenkins.war --httpPort=9090
obs: por default a porta é 8080

# Job de teste
Criado para se realizar os testes da aplicação a cada minuto.
Em Source Code Management foi referenciado o repositório Git do projeto, branch main;
Em Build Triggers, foi colocado em Poll SCM: * * * * *
Em Build, Invoke top-level Maven targets: clean test
Em Post-Build Actions, Publish JUnit test result report: target/surefire-reports/*.xml

# Job de Deploy
Em Source Code Management foi referenciado o repositório Git do projeto, branch main;
Em Build:
	Invoke top-level Maven targets: clean package
	Execute Windows batch command: java -Dspring.profiles.active=prod -jar target/leilao-0.0.1-SNAPSHOT.jar&