# **Spring Cloud Config Server com GitHub**  

Este repositório contém um **Spring Cloud Config Server**, que gerencia e centraliza as configurações das aplicações, utilizando um repositório GitHub como backend.  

## **📌 O que é o Spring Cloud Config Server?**  

O **Spring Cloud Config Server** permite **externalizar e centralizar configurações** das aplicações, evitando a necessidade de alteração manual em cada instância quando executadas em **ambientes distribuídos ou clusterizados**.  

Ele age como uma **API HTTP**, fornecendo os valores de configuração para outras aplicações de forma dinâmica.  

---

## **🛠 Configuração do Servidor**  

O servidor está configurado para buscar as configurações em um repositório do GitHub.  

Trecho relevante do `application.yml`:  

```yaml
server:
  port: 8888

spring:
  application:
    name: aula-config-server
  cloud:
    config:
      server:
        git:
          uri: https://github.com/MiguelHonorio/config-server-with-github
          # username: username
          # password: password
          search-paths: 'greeting-service*'
```

---

## **🧪 Testando a Aplicação**  

Para testar o funcionamento do **Config Server**, utilize as seguintes aplicações:  

1. **config-server** (porta `8888`) - Servidor de configuração que busca os valores do GitHub.  
2. **greeting-service** (porta `8080`) - Aplicação cliente que consome as configurações centralizadas.  

### **Passo a passo:**  

1. **Inicie o `config-server`**  
   - Certifique-se de que ele está apontando para o repositório correto no GitHub.  
2. **Inicie o `greeting-service`**  
   - Ele buscará suas configurações no `config-server`.  
3. **Acesse a URL de configuração** para verificar os valores carregados:  
   ```sh
   http://localhost:8888/greeting-service/default
   ```

Se tudo estiver correto, a resposta JSON conterá as configurações esperadas.  

---

## **🚀 Benefícios do Spring Cloud Config Server**  

✅ Centralização das configurações.  
✅ Facilidade de gerenciamento em ambientes distribuídos.  
✅ Atualização dinâmica de configurações sem necessidade de restart da aplicação.  
✅ Compatível com repositórios Git para versionamento e rastreabilidade.  

---
