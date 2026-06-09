# eureka-service

Service discovery do Rota Facil. Este servico roda um servidor Netflix Eureka para que gateway e microservicos registrem suas instancias e resolvam chamadas por nome logico, como `lb://auth-service`.

## Para que serve

- Centraliza o registro de instancias dos microservicos.
- Permite que o `gateway-service` roteie usando nomes de servico.
- Facilita descoberta dinamica em ambiente local ou distribuido.

## Porta e nome

- Aplicacao: `eureka-service`
- Porta: `8081`
- URL local: `http://localhost:8081`
- Eureka default zone: `http://localhost:8081/eureka`

## Principais configuracoes

- `eureka.client.register-with-eureka=false`: o servidor nao se registra nele mesmo.
- `eureka.client.fetch.registry=false`: nao busca registry como cliente.
- `eureka.server.enable-self-preservation=false`: self-preservation desativado, util em ambiente de desenvolvimento.
- OTLP/Micrometer habilitados por propriedades `management.*`.

## Endpoints

- `GET /`: dashboard web do Eureka.
- `GET /eureka/**`: API interna do Eureka usada pelos clientes.

## Como rodar

Pre-requisitos:

- Java 21.
- Maven ou wrapper `./mvnw`.

Comando:

```bash
cd eureka-service
./mvnw spring-boot:run
```

ou:

```bash
mvn spring-boot:run
```

Suba este servico antes dos demais microservicos.
