# Projeto MQTT (Broker + Sensor + Subscriber)

## Serviços
- **mqtt-broker** (Eclipse Mosquitto 2.0.20), com persistência e logs.
- **temperature-sensor-1** (Python 3.12 + Paho MQTT), publica temperatura a cada 5s.
- **mqtt-subscriber** (mosquitto_sub), assina `sensor/#` e mostra mensagens no log.

## Uso
```bash
docker compose up -d --build
docker compose logs -f mqtt-subscriber
```

## Notas
- Porta 1883 exposta no host. Se não precisar, remova `ports` do broker.
- `allow_anonymous true` apenas para laboratório. Em produção, configure `password_file`, `acl_file` e TLS.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Documentação: Leonado Oliveira Feitosa.

O que foi feito:

- Adicionado autenticação
- Adicionado acl

Primeiramente foi adicionado atenticação, foi criado um arquivo para armazanar um usuário e senha (mosquitto/config/password.txt), logo depois na configuração do arquivo do mosquitto, foi desabilitado "allow_anonymous_true",
e no docker compose também foi refenciado um comando para logar direto, fixando com comando com a senha e o usuário já, para roda é só usar os comandos abaixo:

docker compose up -d --build
<br>
docker compose logs -f mqtt-subscriber


E depois foi adicionado acl, da mesma forma, foi cirado um arquivo e depois referenciado no arquivo de configuração do mosquitto, assim permitindo que o usuario "leo" tem permissão para ler e escrever em todos os sensores.
 

