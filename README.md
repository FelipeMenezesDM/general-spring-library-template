# Auth Server Connect
Biblioteca de integração com o Auth Server para geração de tokens de acesso ou validação de tokens de acesso em rotas autenticadas.

## Tópicos
- [Instalação com Maven](#instalação-com-maven)
- [Deploy manual](#deploy-manual)

## Instalação com Maven
Crie o arquivo de configuração do maven ou inclua o repositório no arquivo já existente:

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">

  <activeProfiles>
    <activeProfile>github</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>github</id>
      <repositories>
        <repository>
          <id>central</id>
          <url>https://repo1.maven.org/maven2</url>
        </repository>
        <repository>
          <id>github</id>
          <url>https://maven.pkg.github.com/felipemenezesdm/general-maven-library-template</url>
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>

  <servers>
    <server>
      <id>github</id>
      <username>${your.username}</username>
      <password>${your.token}</password>
    </server>
  </servers>
</settings>
```

Não esqueça de substituir _${your.username}_ e _${your.token}_ por suas credenciais. Após isso, execute o comando abaixo para baixar as dependências:
```
mvn install
```

Inclua a dependência no arquivo pom:
```xml
<dependency>
  <groupId>br.com.felipemenezesdm</groupId>
  <artifactId>general-maven-library-template</artifactId>
  <version>1.0.0</version>
</dependency>
```

## Deploy manual
Para realizar o deploy manual desta biblioteca, basta executar o comando abaixo, substuindo os parâmetros por seus respectivos valores:

```
mvn deploy -s settings.xml -Dpkg.version="$version" -Drepo.usrnm="$username" -Drepo.pswd="$password"
```