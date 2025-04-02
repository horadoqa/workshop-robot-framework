# workshop-robot-framework

### **Instruções para Roteiro de Testes**

Este roteiro de testes é um guia estruturado para executar testes em um sistema, com foco no planejamento, execução, avaliação e conclusão de testes. Siga os passos abaixo para realizar um teste eficiente.

---

### **1. Escolher um Projeto**

Primeiramente, é necessário escolher um sistema ou aplicação para realizar os testes. A seguir estão dois exemplos de projetos para teste:

- **[Serverest](https://serverest.dev/)**: Um sistema que oferece uma API de gerenciamento de usuários e produtos.
- **[OrangeHRM Demo](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)**: Um sistema de gestão de recursos humanos, com funcionalidades para login e administração de funcionários.

**Ação:**
- Selecione o projeto para o qual você deseja realizar os testes.

---

### **2. Escrever os Requisitos**

Após escolher o projeto, o próximo passo é definir os requisitos que o sistema deve atender. Requisitos podem ser funcionalidades do sistema, comportamentos esperados ou requisitos de desempenho. Exemplos de requisitos podem ser:

- **Requisitos Funcionais**: O sistema deve permitir login com um nome de usuário e senha válidos.
- **Requisitos Não Funcionais**: O sistema deve responder a uma requisição de login em até 2 segundos.
- **Requisitos de Segurança**: O sistema deve criptografar a senha do usuário.

**Ação:**
- Escreva os requisitos específicos que você espera que o sistema cumpra. Seja claro e específico em relação a cada requisito.

---

### **3. Planejamento de Testes**

No planejamento de testes, você precisa determinar quais tipos de testes serão realizados e como serão executados. Isso inclui definir o escopo, os objetivos e os critérios de sucesso.

**Ação:**
- **Defina o tipo de teste**: Testes funcionais, testes de integração, testes de performance, testes de segurança, etc.
- **Escolha as ferramentas de teste**: Ferramentas para automação (ex: Selenium, Postman, Jest) ou testes manuais.
- **Estabeleça o cronograma de testes**: Determine quando e como os testes serão realizados, identificando recursos necessários.

---

### **4. Configuração do Ambiente de Teste**

Antes de iniciar os testes, é essencial configurar o ambiente. Isso pode incluir a instalação de dependências, configuração de servidores, banco de dados e ferramentas de teste. Dependendo do tipo de teste, o ambiente pode ser local ou em servidores de testes.

**Ação:**
- **Ambiente Local**: Se for um teste de API, instale o Postman ou Insomnia. Se for teste funcional, prepare o ambiente de desenvolvimento (IDE, browser).
- **Ambiente de Testes**: Caso esteja utilizando ferramentas como Jenkins ou um servidor de integração contínua, certifique-se de que o ambiente esteja configurado corretamente.

---

### **5. Execução de Testes**

Com o planejamento e ambiente configurados, é hora de executar os testes. Dependendo do escopo, a execução pode ser manual ou automatizada. 

**Ação:**
- **Testes Manuais**: Se os testes forem manuais, execute os casos de teste conforme o plano, documentando os resultados.
- **Testes Automatizados**: Caso esteja automatizando os testes, utilize ferramentas como Selenium, Postman (para APIs) ou frameworks como Jest ou Mocha (para testes em JavaScript).

**Exemplo de Teste Manual:**
- Realizar login no sistema OrangeHRM com credenciais válidas.
- Verificar se o sistema redireciona para a página principal do sistema.

**Exemplo de Teste Automatizado (API):**

```robot framework
*** Settings ***
Library           RequestsLibrary

*** Variables ***
${URL}            https://opensource-demo.orangehrmlive.com/web/index.php/auth/login
${USERNAME}       Admin
${PASSWORD}       admin123

*** Test Cases ***
Deve Retornar 200 Ao Realizar Login
    Create Session    mysession    ${URL}
    ${response}=      Post Request    mysession    /web/index.php/auth/login    username=${USERNAME}    password=${PASSWORD}
    Status Should Be  200    ${response}

*** Keywords ***
Status Should Be
    [Arguments]    ${expected_status}    ${response}
    Should Be Equal As Numbers    ${expected_status}    ${response.status_code}

```

---

### **6. Avaliação de Critérios**

Após a execução dos testes, avalie os resultados com base nos critérios de sucesso definidos na etapa de planejamento. Os critérios de avaliação podem incluir:

- **Passou ou Falhou?**: Verifique se o sistema se comportou conforme esperado.
- **Desempenho**: O sistema atendeu aos requisitos de tempo de resposta ou capacidade de carga?
- **Segurança**: O sistema passou nos testes de segurança, como validação de senhas, criptografia e autenticação?

**Ação:**
- Documente se cada requisito foi atendido com sucesso ou se houve falhas. 

---

### **7. Ciclo de Testes**

Testes podem precisar ser repetidos várias vezes ao longo do ciclo de vida do projeto. Após a execução inicial, podem surgir erros ou melhorias no sistema. O ciclo de testes deve ser repetido conforme novas funcionalidades são desenvolvidas ou correções são feitas.

**Ação:**
- **Feedback e Correção**: Com base nas falhas identificadas, envie feedback para os desenvolvedores, que corrigem os problemas.
- **Reteste**: Após a correção, execute novamente os testes para garantir que o erro foi resolvido.

**Exemplo:**
- Se a função de login falhou durante os testes, notifique os desenvolvedores para corrigir o erro de autenticação. Após a correção, reteste a funcionalidade.

---

### **8. Conclusão dos Testes**

Com todos os testes executados, avaliados e corrigidos, você chega à fase de conclusão. Aqui, você prepara um relatório final com os resultados, aprendizados e recomendações. A conclusão dos testes envolve a validação de que os requisitos foram atendidos, o sistema está pronto para produção ou que novas melhorias devem ser feitas.

**Ação:**
- **Relatório de Testes**: Documente os resultados dos testes (passaram ou falharam), as questões encontradas e as soluções propostas.
- **Recomendações**: Se necessário, forneça recomendações para ajustes ou melhorias no sistema com base nos testes realizados.

---

### **Conclusão**

Seguir essas etapas garante que os testes sejam bem planejados, executados e avaliados de maneira eficiente. Independentemente de ser um teste funcional, de desempenho ou de segurança, o processo ajuda a garantir que o sistema atenda aos requisitos e ofereça uma experiência de qualidade para os usuários finais.
