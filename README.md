# Aplicação Empresarial de Agendamento de Tarefas
Aplicação empresarial de agendamento de tarefas na disciplina de Projeto de Software.

# Primeira etapa : Desenvolvimento de REST API , testes unitários e documentação

Será desenvolvida uma REST API em **Spring Boot** que registrará tarefas em um banco de dados **MySQL** .  

A framework **Spring** foi escolhida para atender aos requisitos de estabilidade e segurança, que neste projeto são mais importantes que a velocidade na incorporação de novos *features*. A facilidade de se encontrar programadores Java no mercado também é conveniente para caso a equipe de desenvolvimento precise ser expandida.  

Nesse estágio do desenvolvimento, a API deve permitir operações CRUD sobre o banco de dados de acordo com as permissões de cada usuário, que devem ser autenticados via OAuth2 com Spring Security. Deve ser possível agendar tarefas ( título, descrição, horário inicial, horário final, tags, horários para lembretes ). Existem usuários que só podem receber tarefas, usuários que podem agendar tarefas para si, e usuários que podem atribuir tarefas para si e para todos os outros. Também existem usuários com status de administrador, que podem alterar os privilégios de edição de outros usuários através da REST API.

Para redução de custos operacionais, não utilizaremos instâncias de máquinas virtuais. A API será hospedada como uma aplicação *serverless* no **AWS Lambda** com **Amazon API Gateway** e o banco de dados MySQL funcionará no **Amazon RDS**. 

Nos horários para lembretes, o usuário deve receber notificações via e-mail e/ou SMS através do **Amazon SNS**.

Caso esta configuração apresente problemas com *cold starts* ( lentidão na inicialização da aplicação, devido ao tempo de inicialização da JVM ), não serão necessárias alterações no código. Basta [adicionar Go e GraalsVM](https://engineering.opsgenie.com/run-native-java-using-graalvm-in-aws-lambda-with-golang-ba86e27930bf) na **AWS Lambda** para eliminar os *cold starts*.

![](https://cdn-images-1.medium.com/max/1200/0*EO090B3qfK-U34J2)

# Segunda etapa: Autocomplete  

Será feito um serviço de *autocompletion* para cada campo das tarefas [usando Redis através do **Amazon ElastiCache**](https://aws.amazon.com/blogs/database/creating-a-simple-autocompletion-service-part-one-of-two/). Esse serviço será consumido pelo front-end.

# Terceira etapa: Front-end   

Será criado um front-end em **React** que irá se comunicar com os endpoints da REST API e irá produzir sugestões de autocomplete em tempo real através de requests para o Redis que está no **Amazon ElastiCache**. O front-end será hospedado no **Amazon S3** e terá o acesso viabilizado através do **Amazon CloudFront**, **Amazon Route 53** e **AWS Certificate Manager**.   

# Quarta etapa: Fine-tuning   

Nessa etapa já estará pronto um MVP escalável. Devemos então agregar valor ao produto nessa etapa, incorporando novos requisitos à aplicação de acordo com as necessidades específicas do cliente e/ou público-alvo.
