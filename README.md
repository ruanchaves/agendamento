# Aplicação Empresarial de Agendamento de Tarefas
Aplicação de agendamento de tarefas empresarial na disciplina de Projeto de Software.

# Primeira etapa : Desenvolvimento de REST API  

Será desenvolvida uma REST API em **Spring Boot** que registrará tarefas em um banco de dados **MySQL** .  

A framework **Spring Boot** foi escolhida para atender aos requisitos de estabilidade e segurança, que neste projeto são mais importantes que a rápida incorporação de novos *features*. A facilidade de se encontrar programadores Java no mercado também é conveniente para caso a equipe de desenvolvimento precise ser expandida.  

Para redução de custos operacionais, não utilizaremos instâncias de máquinas virtuais. A API será hospedada como uma aplicação *serverless* no **AWS Lambda** com **AWS API Gateway** e o banco de dados MySQL funcionará no **Amazon RDS**. 

Caso esta configuração apresente problemas com *cold starts* ( lentidão na inicialização da aplicação, devido ao tempo de inicialização da JVM ), não serão necessárias alterações no código. Basta [adicionar Go e GraalsVM](https://engineering.opsgenie.com/run-native-java-using-graalvm-in-aws-lambda-with-golang-ba86e27930bf).

![](https://cdn-images-1.medium.com/max/1200/0*EO090B3qfK-U34J2)
