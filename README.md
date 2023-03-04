# General Spring Library Template
Modelo padrão para criação de bibliotecas para Spring Boot (Maven)

## Tópicos
- [Instalação com Maven](#instalação-com-maven)
- [Deploy manual](#deploy-manual)

## Instalação com Maven
Crie o arquivo de configuração do maven ou inclua o repositório e o servidor no arquivo já existente:
```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" 
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">

  <activeProfiles>
    <activeProfile>general</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>general</id>
      <repositories>
        <repository>
          <id>central</id>
          <url>https://repo1.maven.org/maven2</url>
        </repository>
        <repository>
          <id>github</id>
          <url>https://maven.pkg.github.com/felipemenezesdm/general-spring-library-template</url>
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>
</settings>
```

Inclua a dependência no arquivo pom:
```xml
<dependency>
  <groupId>br.com.felipemenezesdm</groupId>
  <artifactId>general-spring-library-template</artifactId>
  <version>1.0.0</version>
</dependency>
```

Execute com comando abaixo para download de dependências:
```
mvn install
```

## Deploy manual
O deploy da biblioteca é realizado automaticamente sempre que houver a criação de uma nova tag de versão. Entretanto, se for necessário realizar seu deploy manual, é preciso seguir os passos abaixo:

1. No _settings.xml_, confirmar que o servidor do GitHub está configurado:
    ```xml
      <servers>
        <server>
          <id>github</id>
          <username>${repo.usrnm}</username>
          <password>${repo.pswd}</password>
        </server>
      </servers>
    ```
2. Executar o comando abaixo, substuindo os parâmetros por seus respectivos valores:
    ```
    mvn deploy -s settings.xml -Drepo.usrnm=USERNAME -Drepo.pswd=PASSWORD
    ```