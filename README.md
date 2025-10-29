# DESAFIO QA BEEDOO 2025

##  Escopo
Validação do **módulo de cursos** em [`https://creative-sherbet-a51eac.netlify.app/`](https://creative-sherbet-a51eac.netlify.app/) cobrindo:
- Cadastro, Listagem e Exclusão
- Validações de dados (campos obrigatórios, formatos, datas, limites)
- Segurança mínima (p.ex. XSS, URL `javascript:`)
- RFE consolidados (funcionalidades ausentes fora do escopo)

##  Decisões para criar as User Stories
- **Base em comportamento do usuário** (CRUD básico de cursos).
- **Riscos percebidos**: validações ausentes (campos, datas, URL), **XSS armazenado**, UX da exclusão (confirmação).
- **RFE vs Bug**: tudo que **não existe no escopo** (ex.: “Editar” e **modal de confirmação**) foi classificado como **RFE**. O que existe, mas **falha**, foi classificado como **BUG**.
- **Prioridade** guiada por impacto: segurança/consistência de dados > cadastro > exclusão > UI.

##  User Stories
Veja `docs/USER_STORIES.md` (com critérios de aceitação em Gherkin).

##  Casos de teste
- Planilha (Google Sheets): **[[LINK DA PLANILHA](https://docs.google.com/spreadsheets/d/1IFP406HxHvCxfDRIIRIK-XRMz3UyOoBAmabWJq3toE0/edit?usp=sharing)]**
- Padrão: ID, Cenário, Pré-condição, Passos, Dados de teste, Resultado esperado/obtido, Evidências, Severidade, Status.

##  Execução (passo a passo + como gravar)
- Guia rápido e roteiro de gravação em `docs/TEST_EXECUTION.md`.
- Todas as **evidências (MP4/prints)**: **[[LINK DA PASTA DO DRIVE / evidence](https://drive.google.com/drive/folders/1FvXUU9q3M5sd4BVJ_PCg9cts4X8uClsu?usp=drive_link)]**

##  Relatório de Bugs
- Consolidado em `docs/BUGS.md` (BUG-001…BUG-020).
- Casos RFE consolidados em `docs/RFE.md`.

##  Estratégia de Teste
Resumo e critérios de severidade/prioridade em `docs/TEST_STRATEGY.md`.

---

### Ambiente
- Navegador: **Microsoft Edge 141.0.3537.99 (64 bits)**
- Fuso: **UTC-3 (Brasil)**
- Orientação de execução: janela anônima, zoom 100%, limpar storage a cada caso.

