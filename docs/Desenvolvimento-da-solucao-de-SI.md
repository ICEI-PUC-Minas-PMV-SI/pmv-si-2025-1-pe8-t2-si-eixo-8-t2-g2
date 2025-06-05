## Apresentação da solução que será desenvolvida

A solução proposta para a Conviver Complexo de Atenção ao Idoso será composta por uma parte sistêmica e uma parte em BI. Com este contexto, a parte sistêmica será responsável pelo cadastro das informações nos bancos de dados utilizados, bem como a administração das informações sobre os residentes sob o cuidado dos profissionais, enquanto o BI irá gerar relatórios e alertas, além de uma visão em tempo real das informações contidas no Banco de Dados da Conviver.  
A escolha por este modelo híbrido foi tomada para que pudéssemos utilizar os benefícios de ambas as estruturas.  
Por um lado, a Inteligência Competitiva, acompanhamento de números e alertas simplificados, proporcionada por uma aplicação BI irá auxiliar a tomada de decisões e maior eficiência dos recursos da empresa, uma vez que a gestão não irá necessitar de empregar muito tempo com levantamento e análises de números de medicamentos em estoque, por exemplo.  
Já a aplicação Web, irá auxiliar através do formato de uma aplicação única, onde, além de abrigar os dados dos residentes, ela também será responsável pela atividade operacional de controle dos estoques de recursos e medicamentos. Além disso, dentro da própria aplicação, os dashboards com as métricas importantes serão visualizados, em uma área interna, para maior controle da informação e disponibilização da mesma para as partes interessadas e autorizadas para seu acesso.  
Outro benefício do modelo híbrido, é que a aplicação Web ainda irá padronizar as informações cadastradas no banco de dados, permitindo que as análises sejam realizadas através da aplicação BI.  
As escolhas em relação ao modelo de aplicação, se dão justamente pelo baixo custo de operação, que será um diferencial para a Conviver não precisará arcar com altos custos de hospedagem para a aplicação e banco de dados. O sistema foi desenvolvido para se ajustar à própria estrutura de hospedagem do website que possuíam.  
Em relação a viabilidade técnica, a Conviver Complexo de Atenção ao Idoso terá de se dispor a contratar um serviço de consultoria para manutenção da aplicação, uma vez que não dispõe de uma equipe de TI qualificada para tal função. Em relação ao custo desta manutenção, irá depender muito da consultoria contratada, e do serviço a ser realizado.

---

## Tela inicial

![Tela inicial](https://github.com/user-attachments/assets/50ded8d1-693a-429c-aa92-7606b12abfd5)

![TelaInicialBusca](https://github.com/user-attachments/assets/78a91f98-e572-434b-83ca-da84c8c0c9af)

![PacienteCompleto](https://github.com/user-attachments/assets/892094d8-c792-459a-9ce4-4ba0c3f679d2)

---

## Cadastro Medicamentos

![CadMedicamento](https://github.com/user-attachments/assets/f8a6aea3-9895-4b40-a456-006765508c4a)


## Cadastro Paciente

![CadPaciente](https://github.com/user-attachments/assets/868d2bd2-a072-4f95-bb8f-22439595a1e8)


## Cadastro Funcionários

![CadFuncionario](https://github.com/user-attachments/assets/cb1f4a1c-7a0a-4293-89d1-6cd5c5e65328)


## Relatórios

### Relatório Estoque

![RelaEstoque](https://github.com/user-attachments/assets/02a947e3-a6d1-451c-b82f-5f90a56cd09e)


### Relatório Movimentação

![RelaMovimenta](https://github.com/user-attachments/assets/c8b9af95-efcf-4489-aa0f-cc6026c0c652)


---

A estrutura de navegação do sistema foi projetada seguindo um modelo hierárquico com navegação entre módulos principais:

**Tela Inicial (Dashboard):** Ponto central de acesso com busca rápida de pacientes e acesso aos principais módulos.

- Botões de acesso rápido para cadastros  
- Campo de busca para localização imediata de pacientes  
- Visualização de alertas críticos (estoque baixo)  

**Fluxo Principal de Navegação:**

- Dashboard → Cadastro/Busca de Paciente → Detalhes do Paciente → Gerenciamento de Medicamentos do Paciente  
- Dashboard → Estoque de Itens → Gerenciamento de Estoque  
- Dashboard → Relatórios → Logs de Movimentação/Notificações  

Este fluxo permite que os profissionais acessem rapidamente as informações mais relevantes para tomada de decisão, como estoque crítico e necessidades específicas dos pacientes.

---

## Armazenamento e Acesso aos Dados

**Tabelas Ex.:**

![TabFunciona](https://github.com/user-attachments/assets/370c2b8e-8f95-423b-859f-a4cf97b5b7ba)

![TabMedicament](https://github.com/user-attachments/assets/5c3afa36-4ede-4a15-b3d6-a135b278380d)

![TabPaciente](https://github.com/user-attachments/assets/bb4b8375-e7f3-460c-8b2f-5fdfa549722b)

![TabRelatorio](https://github.com/user-attachments/assets/5c70e6ce-d834-4e27-a854-68809cb79374)


O sistema utiliza um banco de dados relacional (SQL Server) com as seguintes características:

**Estrutura de Dados:**

- Tabelas principais: Paciente, Medicamento, Funcionário  
- Tabelas de relacionamento: Paciente_Medicamento (associação N:N)  
- Tabelas de monitoramento: LogEstoqueMedicamento, Notificacao  

**Acesso aos Dados:**

- Padrão Repository através do Entity Framework Core

---

# ETAPA 4: Preparação do Desenvolvimento

## Divisão de tarefas:

- Alisson Pereira Machado - Mockups e Front End.  
- Bruno Antônio Ávila Silva - Documentação e Banco de dados.  
- Geraldo de Souza Paula - Testes e correção de bugs.  
- Lucas de Souza Chagas Lima - Diagramas, Backend e Banco de dados.  
- Lucas Santos Guimarães - Deploy e configs do ambiente da aplicação.  
- Vinicius de Oliveira Inocêncio - Deploy e configs do ambiente da aplicação.

## Plano de Execução: Ordem de Implementação

A implementação seguiu uma abordagem incremental baseada em prioridades de negócio:

### Fase 1 - Estrutura Base e Cadastros:

- Modelagem do banco de dados  
- Implementação dos Models e DbContext  
- CRUD básico de Pacientes, Funcionários e Medicamentos

### Fase 2 - Gestão de Relacionamentos:

- Vínculo Paciente-Medicamento  
- Controle de estoque individual por paciente  
- Definição de doses diárias e quantidades críticas

### Fase 3 - Monitoramento e Alertas:

- Sistema de logs de movimentação  
- Notificações de estoque crítico  
- Relatórios de consumo

### Fase 4 - Inteligência de Negócio:

- Dashboard com indicadores-chave  
- Previsão de consumo baseada em histórico  
- Alertas preventivos

---

# ETAPA 5: Geração de Relatórios Internos


![RelaEstoque](https://github.com/user-attachments/assets/7bab4379-c921-4803-a961-f684d64425dc)

![RelaMovimenta](https://github.com/user-attachments/assets/24550bd8-c6da-4707-a833-9b549fe96f99)


O sistema oferece diversos recursos que auxiliam na tomada de decisão estratégica:

### Exemplo 1: Identificação de Estoque Crítico

- O sistema destaca visualmente (em vermelho) itens com estoque abaixo do limite crítico  
- Permite identificar rapidamente quais medicamentos precisam de reposição urgente  
- Facilita o planejamento de compras baseado em prioridades reais

### Exemplo 2: Monitoramento de Consumo por Paciente

- Através dos logs de movimentação, é possível analisar o padrão de consumo de cada paciente  
- Permite identificar anomalias no uso de medicamentos (consumo acima ou abaixo do esperado)  
- Auxilia na revisão de prescrições e ajustes de doses

### Exemplo 3: Previsão de Necessidades Futuras

- Com base no histórico de consumo e nas doses diárias configuradas, o sistema pode projetar necessidades futuras  
- Permite planejamento antecipado de compras, evitando falta de itens essenciais  
- Otimiza o fluxo de caixa ao evitar compras emergenciais (geralmente mais caras)

### Exemplo 4: Rastreabilidade Completa

- O sistema mantém logs detalhados de todas as movimentações de estoque  
- Permite auditoria completa do ciclo de vida dos medicamentos  
- Facilita a identificação de possíveis desvios ou uso inadequado

---

## REFERÊNCIAS

- ASSOCIAÇÃO BRASILEIRA DE NORMAS TÉCNICAS.  
  ABNT NBR ISO/IEC 27001:2022 – Tecnologia da informação – Técnicas de segurança – Sistemas de gestão de segurança da informação – Requisitos.  
  Rio de Janeiro: ABNT, 2022.

- BRASIL.  
  Lei nº 13.709, de 14 de agosto de 2018. Dispõe sobre a proteção de dados pessoais e altera a Lei nº 12.965, de 23 de abril de 2014 (Marco Civil da Internet).  
  Diário Oficial da União: seção 1, Brasília, DF, ano 155, n. 157, p. 1-6, 15 ago. 2018.  
  Disponível em: https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm.  
  Acesso em: 4 abr. 2025.

- CONTABILIZEI. Porte de empresa: quais são os tipos e como identificar o seu.  
  Disponível em: https://www.contabilizei.com.br/contabilidade-online/porte-de-empresa/.  
  Acesso em: 4 mar. 2025.

- CONVIVER IDOSOS. Centro Dia para Idosos.  
  Disponível em: https://conviveridosos.com.br/#s-home.  
  Acesso em: 4 abr. 2025.
**
