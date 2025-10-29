# Estratégia de Teste

## 1. Objetivo
Garantir qualidade funcional, integridade dos dados e sinais mínimos de segurança do módulo de cursos em `https://creative-sherbet-a51eac.netlify.app/`.

## 2. Escopo
- **Incluído**: Cadastro, Listagem, Exclusão; validações (obrigatórios, formatos, datas, limites), UI responsiva básica; segurança leve (XSS/URL).
- **Fora do escopo (RFE)**: Confirmação (modal) de exclusão e Edição de curso.

## 3. Abordagem
- **Funcional**: fluxos principais (happy path) e de erro (negativos).
- **UI/UX**: consistência visual (alinhamento de cards, titulação, truncamento).
- **Segurança leve**: XSS armazenado, URL com esquema inválido.
- **Técnico**: observar Console/Network (DELETE 405 etc.).

## 4. Técnicas e Heurísticas
- Particionamento de equivalência; valores-limite (min/max caracteres; datas; inteiros em vagas);
- “Anti-cases”: `javascript:`, sem protocolo; campos só com espaços; trocas de Tipo (Presencial/Online).

## 5. Severidade (resumo)
- **Crítico**: Falhas que comprometem segurança/fluxo principal (XSS, ausência de validação essencial, API 405).
- **Alto**: Inconsistência grave de regra (fim < início, datas inválidas aceitas).
- **Médio**: UX/Layout desalinhado; estado de botão incorreto.
- **Baixo**: Cosméticos/typos.

## 6. Ambiente e Padrões de Execução
- **Navegador**: Microsoft Edge 141.0.3537.99 (64 bits) — janela anônima; zoom 100%.
- **Antes de cada caso**: DevTools → Application → *Clear storage* → Clear site data.
- **Gravação**: 1080p/1440p, 30fps; evidências em MP4.

## 7. Artefatos de Referência
- **User Stories**: `docs/USER_STORIES.md`
- **Casos de Teste (planilha)**: [LINK_PLANILHA]
- **Evidências (Drive)**: [LINK_DRIVE_VIDEOS](https://drive.google.com/drive/folders/1Z1ZPmy_yVhLAgw-hWNR0IbD2ISPO2PFq?usp=drive_link), [LINK_DRIVE_PRINTS](https://drive.google.com/drive/folders/1iCO2TnTT6n7bSpIS4rO98jmZMMa3b51_?usp=drive_link)

## 8. Critérios de Aceite
- Todos os **casos críticos/altos** executados com evidência.
- Bugs documentados com repro passo-a-passo e link para prova (vídeo/print).
- RFEs separados de BUGs.

## 9. Rastreabilidade
- Tags `@CAD-###` nos cenários do `USER_STORIES.md` ↔ IDs da planilha ↔ evidências no Drive.
