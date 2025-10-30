# DESAFIO QA BEEDOO 2025

> **Alvo:** https://creative-sherbet-a51eac.netlify.app/  
> **Navegador:** Microsoft Edge 141.0.3537.99 (64 bits)  
> **Fuso:** UTC-3 (Brasil)  
> **Autor:** Lucas Mateus

##  Links rápidos
- **Planilha de Casos de Teste (Google Sheets):** [Casos de Testes](https://docs.google.com/spreadsheets/d/1IFP406HxHvCxfDRIIRIK-XRMz3UyOoBAmabWJq3toE0/edit?usp=sharing)
- **Evidências (Drive — vídeos & prints):** [Evidências](https://drive.google.com/drive/folders/1FvXUU9q3M5sd4BVJ_PCg9cts4X8uClsu?usp=drive_link)
- **User Stories (Gherkin):** [docs/USER_STORIES.md](docs/USER_STORIES.md)
- **Estratégia de Teste:** [docs/TEST_STRATEGY.md](docs/TEST_STRATEGY.md)
- **Execução (passo a passo):** [docs/TEST_EXECUTION.md](docs/TEST_EXECUTION.md)
- **Relatório de Bugs:** [docs/BUGS.md](docs/BUGS.md)
- **RFEs (melhorias):** [docs/RFE.md](docs/RFE.md)

---

##  Escopo
Validação do **módulo de cursos** cobrindo:
- Cadastro, Listagem e Exclusão
- Validações de dados (obrigatórios, formatos, datas, limites)
- Segurança mínima (ex.: XSS, URL `javascript:`)
- RFEs consolidados (funcionalidades ausentes fora do escopo)

##  Decisões para criar as User Stories
- **Base em comportamento do usuário** (CRUD de cursos).
- **Riscos percebidos**: validações ausentes (campos, datas, URL), **XSS armazenado**, UX da exclusão.
- **RFE vs Bug**: o que **não existe** no escopo (ex.: **Editar**, **modal de confirmação**) ⇒ **RFE**.  
  O que existe mas **falha** ⇒ **BUG**.
- **Prioridade** por impacto: segurança/consistência de dados > cadastro > exclusão > UI.

##  User Stories
Critérios de aceitação em Gherkin: [docs/USER_STORIES.md](docs/USER_STORIES.md)

##  Casos de teste
- Planilha oficial: **Google Sheets** (acesso leitura) [Casos de Testes](https://docs.google.com/spreadsheets/d/1IFP406HxHvCxfDRIIRIK-XRMz3UyOoBAmabWJq3toE0/edit?usp=sharing)
- Padrão de colunas: **ID, Cenário, Pré-condição, Passos, Dados de teste, Resultado esperado/obtido, Evidência, Severidade, Status**.

##  Execução (passo a passo + gravação)
- Guia completo: [docs/TEST_EXECUTION.md](docs/TEST_EXECUTION.md)
- **Evidências (apenas vídeos & prints):** [Pasta do Drive](https://drive.google.com/drive/folders/1mdZ4u2FHJHIT4UhbbGnn7J3cnabul3ny?usp=drive_link)

**Padrões de evidência**
- **Vídeos**: `evidence/videos/CAD/CAD-XYZ.mp4`
- **Prints (RFE/Blocked/UI)**: `evidence/prints/CAD-XYZ.png`
- **Nomenclatura sugerida**: `AAAA-MM-DD_CAD-XYZ_Status_Res.mp4` (opcional)

##  Relatório de Bugs
Consolidado em: [docs/BUGS.md](docs/BUGS.md)  
> Observação: quando houver **mais de um link** por bug (vídeo + print), os links são listados na mesma célula (ex.: `🎥 Vídeo · 🖼️ Print`).

##  RFEs (melhorias, fora do escopo)
Lista e critérios em: [docs/RFE.md](docs/RFE.md)

---

##  Ambiente de teste
- Navegador: **Microsoft Edge 141.0.3537.99 (64 bits)**
- Execução em **janela anônima**, **zoom 100%**
- **Limpar storage** antes de cada caso (DevTools → Application → Clear storage → Clear site data)

##  Rastreabilidade
- IDs `@CAD-###` nas User Stories ↔ linhas da planilha ↔ arquivos de evidência no Drive.

