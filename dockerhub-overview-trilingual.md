# IronGrid Limited 369

**Tutorial / Manual HTML:**

- Portugues: https://sachelaride.github.io/IronGrid-369/index.html
- English: https://sachelaride.github.io/IronGrid-369/index-en.html
- Espanol: https://sachelaride.github.io/IronGrid-369/index-es.html

---

## Idiomas / Languages / Idiomas

- [Portugues](#portugues)
- [English](#english)
- [Espanol](#espanol)

---

## Portugues

Edicao limitada do IronGrid, disponibilizada gratuitamente para a comunidade por meio do Docker Hub.

O IronGrid e uma plataforma voltada para monitoramento e gerenciamento de infraestrutura de redes e servidores, reunindo recursos como SNMP, Syslog, inventario de ativos, IPAM, metricas, Grafana e integracao com RustDesk.

A IronGrid Limited 369 e uma edicao funcional, preparada para utilizacao em ambientes reais, com limites especificos em relacao a versao completa.

### Imagem Docker

A imagem oficial da edicao limitada esta disponivel no Docker Hub:

```text
sachelaride/irongrid-limited-369
```

Tags disponiveis:

```text
sachelaride/irongrid-limited-369:latest
sachelaride/irongrid-limited-369:limited-369
```

Para ambientes de producao que exigem previsibilidade, prefira uma tag especifica:

```yaml
image: sachelaride/irongrid-limited-369:limited-369
```

Para acompanhar a versao mais recente:

```yaml
image: sachelaride/irongrid-limited-369:latest
```

**Atencao:** a tag `latest` podera receber atualizacoes futuras.

### O que esta incluido

- frontend da aplicacao
- backend
- gerenciamento de ativos
- monitoramento de rede
- monitoramento SNMP
- Syslog
- agentes para download
- integracoes do IronGrid
- integracao com Grafana
- integracao com RustDesk
- recursos de inventario e gerenciamento de infraestrutura

### Requisitos

A instalacao deve ser realizada em um servidor Linux com suporte ao Docker.

```bash
sudo apt update
sudo apt install -y docker.io docker-compose-plugin openssl
sudo systemctl enable --now docker
docker --version
docker compose version
```

### Instalacao rapida

Crie o diretorio da instalacao:

```bash
sudo mkdir -p /opt/irongrid
cd /opt/irongrid
```

Crie o arquivo `.env`:

```bash
nano .env
```

Use senhas e tokens proprios e fortes:

```env
NODE_ENV=production
DEV_PORT=3001
DEBUG=false

IRONGRID_EDITION=limited
IRONGRID_GRAFANA_CHART_LIMIT=69

IRONGRID_HTTP_PORT=3001
IRONGRID_SYSLOG_PORT=514

POSTGRES_USER=irongrid
POSTGRES_PASSWORD=TROQUE_POR_SENHA_FORTE
POSTGRES_DB=irongrid_db

DATABASE_URL=postgresql://irongrid:TROQUE_POR_SENHA_FORTE@db:5432/irongrid_db?schema=public
SYSLOG_DATABASE_URL=postgresql://irongrid:TROQUE_POR_SENHA_FORTE@db:5432/irongrid_db?schema=public

JWT_SECRET=TROQUE_POR_SEGREDO_FORTE_32_CHARS_OU_MAIS
AGENT_INGEST_TOKEN=TROQUE_POR_TOKEN_FORTE_16_CHARS_OU_MAIS

ALLOWED_ORIGIN=http://IP_DO_SERVIDOR:3001

INFLUX_URL=http://influxdb:8086
INFLUX_INIT_USERNAME=admin
INFLUX_INIT_PASSWORD=TROQUE_POR_SENHA_FORTE_INFLUX
INFLUX_ORG=irongrid
INFLUX_BUCKET=metrics
INFLUX_TOKEN=TROQUE_POR_TOKEN_FORTE_INFLUX

GRAFANA_PORT=3000

RUSTDESK_HBBS_PORT=21115
RUSTDESK_RENDEZVOUS_TCP_PORT=21116
RUSTDESK_RENDEZVOUS_UDP_PORT=21116
RUSTDESK_RELAY_PORT=21117
RUSTDESK_WEB_CLIENT_PORT=21118
RUSTDESK_RELAY_WEB_PORT=21119
```

Crie o arquivo `docker-compose.yml` conforme o tutorial completo:

https://sachelaride.github.io/IronGrid-369/index.html

Valide e inicie:

```bash
docker compose config
docker compose pull
docker compose up -d
docker compose ps
```

Para iniciar tambem Grafana e RustDesk:

```bash
docker compose pull
docker compose --profile full up -d
docker compose ps
```

### Acesso

Abra no navegador:

```text
http://IP_DO_SERVIDOR:3001
```

Login inicial:

```text
Usuario: admin
Senha: admin
```

### RustDesk

Quando o IronGrid for iniciado com o perfil `remote` ou `full`, obtenha a chave publica:

```bash
docker cp irongrid-hbbs:/root/id_ed25519.pub ./id_ed25519.pub
cat ./id_ed25519.pub
```

A chave publica deve ser usada na tela Gestao de Agentes do IronGrid. A chave privada `id_ed25519` deve permanecer protegida no servidor.

### Gerenciamento basico

```bash
docker compose ps
docker compose logs -f --tail=200 app
docker compose restart
docker compose down
docker compose up -d
docker compose --profile full up -d
```

### Apoie o projeto

O desenvolvimento e a manutencao do IronGrid demandam tempo, infraestrutura, equipamentos para testes e recursos para continuidade do projeto.

Contribuicao via PIX:

```text
PIX CPF: 558252491-68
PIX E-mail: sachelaride@gmail.com
```

Contribuicao internacional em USD:

```text
Beneficiario: GERMAN DE OLIVEIRA SACHELARIDE
Banco beneficiario: Banco Inter S.A.
SWIFT: ITEMBRSP
IBAN: BR2800416968000010011233613C1
Banco intermediario: JP Morgan Chase N.A.
SWIFT banco intermediario: CHASUS33
ABA: 021000021
Account: 360556937
```

### Suporte e contato

German Sachelaride - Analista de Network

```text
E-mail: sachelaride@gmail.com
Telefone: (67) 9.9859-9051
```

IronGrid Limited 369 - Monitoramento, Gestao, SNMP, Syslog, Grafana e RustDesk.

---

## English

IronGrid Limited 369 is a limited edition of IronGrid, made available for free to the community through Docker Hub.

IronGrid is a platform for monitoring and managing network and server infrastructure. It brings together SNMP, Syslog, asset inventory, IPAM, metrics, Grafana, and RustDesk integration.

IronGrid Limited 369 is a functional edition prepared for real environments, with specific limits compared to the full version.

### Docker Image

Official limited edition image:

```text
sachelaride/irongrid-limited-369
```

Available tags:

```text
sachelaride/irongrid-limited-369:latest
sachelaride/irongrid-limited-369:limited-369
```

For production environments that require predictability, prefer the fixed edition tag:

```yaml
image: sachelaride/irongrid-limited-369:limited-369
```

To follow the most recent version:

```yaml
image: sachelaride/irongrid-limited-369:latest
```

**Warning:** the `latest` tag may receive future updates.

### What is included

- application frontend
- backend
- asset management
- network monitoring
- SNMP monitoring
- Syslog
- downloadable agents
- IronGrid integrations
- Grafana integration
- RustDesk integration
- inventory and infrastructure management features

### Requirements

Installation must be performed on a Linux server with Docker support.

```bash
sudo apt update
sudo apt install -y docker.io docker-compose-plugin openssl
sudo systemctl enable --now docker
docker --version
docker compose version
```

### Quick Installation

Create the installation directory:

```bash
sudo mkdir -p /opt/irongrid
cd /opt/irongrid
```

Create the `.env` file:

```bash
nano .env
```

Use your own strong passwords and tokens:

```env
NODE_ENV=production
DEV_PORT=3001
DEBUG=false

IRONGRID_EDITION=limited
IRONGRID_GRAFANA_CHART_LIMIT=69

IRONGRID_HTTP_PORT=3001
IRONGRID_SYSLOG_PORT=514

POSTGRES_USER=irongrid
POSTGRES_PASSWORD=REPLACE_WITH_STRONG_PASSWORD
POSTGRES_DB=irongrid_db

DATABASE_URL=postgresql://irongrid:REPLACE_WITH_STRONG_PASSWORD@db:5432/irongrid_db?schema=public
SYSLOG_DATABASE_URL=postgresql://irongrid:REPLACE_WITH_STRONG_PASSWORD@db:5432/irongrid_db?schema=public

JWT_SECRET=REPLACE_WITH_STRONG_SECRET_32_CHARS_OR_MORE
AGENT_INGEST_TOKEN=REPLACE_WITH_STRONG_TOKEN_16_CHARS_OR_MORE

ALLOWED_ORIGIN=http://SERVER_IP:3001

INFLUX_URL=http://influxdb:8086
INFLUX_INIT_USERNAME=admin
INFLUX_INIT_PASSWORD=REPLACE_WITH_STRONG_INFLUX_PASSWORD
INFLUX_ORG=irongrid
INFLUX_BUCKET=metrics
INFLUX_TOKEN=REPLACE_WITH_STRONG_INFLUX_TOKEN

GRAFANA_PORT=3000

RUSTDESK_HBBS_PORT=21115
RUSTDESK_RENDEZVOUS_TCP_PORT=21116
RUSTDESK_RENDEZVOUS_UDP_PORT=21116
RUSTDESK_RELAY_PORT=21117
RUSTDESK_WEB_CLIENT_PORT=21118
RUSTDESK_RELAY_WEB_PORT=21119
```

Create the `docker-compose.yml` file according to the full tutorial:

https://sachelaride.github.io/IronGrid-369/index-en.html

Validate and start:

```bash
docker compose config
docker compose pull
docker compose up -d
docker compose ps
```

To start IronGrid with Grafana and RustDesk:

```bash
docker compose pull
docker compose --profile full up -d
docker compose ps
```

### Access

Open in your browser:

```text
http://SERVER_IP:3001
```

Initial login:

```text
User: admin
Password: admin
```

### RustDesk

When IronGrid is started with the `remote` or `full` profile, get the public key:

```bash
docker cp irongrid-hbbs:/root/id_ed25519.pub ./id_ed25519.pub
cat ./id_ed25519.pub
```

Use this public key in the IronGrid Agent Management screen. The private key `id_ed25519` must remain protected on the server.

### Basic Management

```bash
docker compose ps
docker compose logs -f --tail=200 app
docker compose restart
docker compose down
docker compose up -d
docker compose --profile full up -d
```

### Support the Project

IronGrid development and maintenance require time, infrastructure, test equipment, and resources to keep the project moving forward.

PIX contribution:

```text
PIX CPF: 558252491-68
PIX E-mail: sachelaride@gmail.com
```

International USD contribution:

```text
Beneficiary: GERMAN DE OLIVEIRA SACHELARIDE
Beneficiary bank: Banco Inter S.A.
SWIFT: ITEMBRSP
IBAN: BR2800416968000010011233613C1
Intermediary bank: JP Morgan Chase N.A.
Intermediary bank SWIFT: CHASUS33
ABA: 021000021
Account: 360556937
```

### Support and Contact

German Sachelaride - Network Analyst

```text
E-mail: sachelaride@gmail.com
Phone: +55 67 99859-9051
```

IronGrid Limited 369 - Monitoring, Management, SNMP, Syslog, Grafana, and RustDesk.

---

## Espanol

IronGrid Limited 369 es una edicion limitada de IronGrid, disponible gratuitamente para la comunidad a traves de Docker Hub.

IronGrid es una plataforma para monitoreo y gestion de infraestructura de redes y servidores. Reune SNMP, Syslog, inventario de activos, IPAM, metricas, Grafana e integracion con RustDesk.

IronGrid Limited 369 es una edicion funcional, preparada para uso en entornos reales, con limites especificos en comparacion con la version completa.

### Imagen Docker

Imagen oficial de la edicion limitada:

```text
sachelaride/irongrid-limited-369
```

Tags disponibles:

```text
sachelaride/irongrid-limited-369:latest
sachelaride/irongrid-limited-369:limited-369
```

Para entornos de produccion que requieren previsibilidad, prefiera la tag fija de la edicion:

```yaml
image: sachelaride/irongrid-limited-369:limited-369
```

Para seguir la version mas reciente:

```yaml
image: sachelaride/irongrid-limited-369:latest
```

**Atencion:** la tag `latest` puede recibir actualizaciones futuras.

### Que esta incluido

- frontend de la aplicacion
- backend
- gestion de activos
- monitoreo de red
- monitoreo SNMP
- Syslog
- agentes para descarga
- integraciones de IronGrid
- integracion con Grafana
- integracion con RustDesk
- recursos de inventario y gestion de infraestructura

### Requisitos

La instalacion debe realizarse en un servidor Linux con soporte para Docker.

```bash
sudo apt update
sudo apt install -y docker.io docker-compose-plugin openssl
sudo systemctl enable --now docker
docker --version
docker compose version
```

### Instalacion rapida

Cree el directorio de instalacion:

```bash
sudo mkdir -p /opt/irongrid
cd /opt/irongrid
```

Cree el archivo `.env`:

```bash
nano .env
```

Use contrasenas y tokens propios y seguros:

```env
NODE_ENV=production
DEV_PORT=3001
DEBUG=false

IRONGRID_EDITION=limited
IRONGRID_GRAFANA_CHART_LIMIT=69

IRONGRID_HTTP_PORT=3001
IRONGRID_SYSLOG_PORT=514

POSTGRES_USER=irongrid
POSTGRES_PASSWORD=REEMPLAZAR_POR_CONTRASENA_SEGURA
POSTGRES_DB=irongrid_db

DATABASE_URL=postgresql://irongrid:REEMPLAZAR_POR_CONTRASENA_SEGURA@db:5432/irongrid_db?schema=public
SYSLOG_DATABASE_URL=postgresql://irongrid:REEMPLAZAR_POR_CONTRASENA_SEGURA@db:5432/irongrid_db?schema=public

JWT_SECRET=REEMPLAZAR_POR_SECRETO_SEGURO_32_CHARS_O_MAS
AGENT_INGEST_TOKEN=REEMPLAZAR_POR_TOKEN_SEGURO_16_CHARS_O_MAS

ALLOWED_ORIGIN=http://IP_DEL_SERVIDOR:3001

INFLUX_URL=http://influxdb:8086
INFLUX_INIT_USERNAME=admin
INFLUX_INIT_PASSWORD=REEMPLAZAR_POR_CONTRASENA_SEGURA_INFLUX
INFLUX_ORG=irongrid
INFLUX_BUCKET=metrics
INFLUX_TOKEN=REEMPLAZAR_POR_TOKEN_SEGURO_INFLUX

GRAFANA_PORT=3000

RUSTDESK_HBBS_PORT=21115
RUSTDESK_RENDEZVOUS_TCP_PORT=21116
RUSTDESK_RENDEZVOUS_UDP_PORT=21116
RUSTDESK_RELAY_PORT=21117
RUSTDESK_WEB_CLIENT_PORT=21118
RUSTDESK_RELAY_WEB_PORT=21119
```

Cree el archivo `docker-compose.yml` segun el tutorial completo:

https://sachelaride.github.io/IronGrid-369/index-es.html

Valide e inicie:

```bash
docker compose config
docker compose pull
docker compose up -d
docker compose ps
```

Para iniciar IronGrid con Grafana y RustDesk:

```bash
docker compose pull
docker compose --profile full up -d
docker compose ps
```

### Acceso

Abra en el navegador:

```text
http://IP_DEL_SERVIDOR:3001
```

Login inicial:

```text
Usuario: admin
Contrasena: admin
```

### RustDesk

Cuando IronGrid se inicia con el perfil `remote` o `full`, obtenga la clave publica:

```bash
docker cp irongrid-hbbs:/root/id_ed25519.pub ./id_ed25519.pub
cat ./id_ed25519.pub
```

Use esta clave publica en la pantalla Gestion de Agentes de IronGrid. La clave privada `id_ed25519` debe permanecer protegida en el servidor.

### Gestion basica

```bash
docker compose ps
docker compose logs -f --tail=200 app
docker compose restart
docker compose down
docker compose up -d
docker compose --profile full up -d
```

### Apoye el proyecto

El desarrollo y mantenimiento de IronGrid requieren tiempo, infraestructura, equipos de prueba y recursos para continuar el proyecto.

Contribucion via PIX:

```text
PIX CPF: 558252491-68
PIX E-mail: sachelaride@gmail.com
```

Contribucion internacional en USD:

```text
Beneficiario: GERMAN DE OLIVEIRA SACHELARIDE
Banco beneficiario: Banco Inter S.A.
SWIFT: ITEMBRSP
IBAN: BR2800416968000010011233613C1
Banco intermediario: JP Morgan Chase N.A.
SWIFT banco intermediario: CHASUS33
ABA: 021000021
Account: 360556937
```

### Soporte y contacto

German Sachelaride - Analista de Network

```text
E-mail: sachelaride@gmail.com
Telefono: +55 67 99859-9051
```

IronGrid Limited 369 - Monitoreo, Gestion, SNMP, Syslog, Grafana y RustDesk.
