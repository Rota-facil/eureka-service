# eureka-service

Servidor Netflix Eureka do Rota Fácil. Mantém o registro das instâncias e permite resolução por nome lógico, como `lb://transport-service`.

## Configuração

- Aplicação: `eureka-service`
- Porta: `8081`
- Dashboard: `http://localhost:8081`
- Default zone: `http://localhost:8081/eureka`

Configuração local: `register-with-eureka=false`, `fetch-registry=false` e `enable-self-preservation=false`. A autopreservação desligada facilita desenvolvimento, mas deve ser reavaliada em produção. Métricas e traces são exportados por OTLP conforme `management.*`.

## Como rodar

```bash
cd eureka-service
./mvnw spring-boot:run
```

Requer Java 21. Suba este serviço antes dos demais quando executar sem Docker Compose.
