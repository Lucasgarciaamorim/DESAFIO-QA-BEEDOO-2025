# User Stories – Módulo de Cursos
<div id="topo"></div>


> **Ambiente:** https://creative-sherbet-a51eac.netlify.app/  
> **Navegador:** Microsoft Edge 141.0.3537.99 (64 bits)  
> **Planilha de Casos de Teste:** [[LINK_PLANILHA](https://docs.google.com/spreadsheets/d/1IFP406HxHvCxfDRIIRIK-XRMz3UyOoBAmabWJq3toE0/edit?usp=drive_link)]  
> **Evidências (Drive):** [[LINK_DRIVE_VIDEOS](https://drive.google.com/drive/folders/1FvXUU9q3M5sd4BVJ_PCg9cts4X8uClsu?usp=drive_link)]

<details>
  <summary><strong>Sumário</strong></summary>

- [Convenções](#convenções)
- [US-001 — Cadastrar curso (Online)](#us-001--cadastrar-curso-online)
- [US-002 — Validações de campos (gerais)](#us-002--validações-de-campos-gerais)
- [US-003 — Tipos Presencial/Online](#us-003--tipos-presencialonline)
- [US-004 — Datas do curso](#us-004--datas-do-curso)
- [US-005 — Listagem de cursos (UI/UX)](#us-005--listagem-de-cursos-uiux)
- [US-006 — Excluir curso (funcional)](#us-006--excluir-curso-funcional)
- [US-007 — Confirmação de exclusão (modal) — RFE](#us-007--confirmação-de-exclusão-modal--rfe)
- [US-008 — Editar curso — RFE](#us-008--editar-curso--rfe)

</details>

## Convenções
- Cada cenário referencia o **ID do caso** (ex.: `@CAD-001`) para facilitar rastreabilidade.
- Itens marcados como **RFE** são melhorias (fora do escopo atual).
- Critérios escritos em **Gherkin** (Given/When/Then).

---

## US-001 — Cadastrar curso (Online)
**Como** operador  
**Quero** cadastrar um curso online  
**Para** que ele apareça corretamente na listagem

```gherkin
@cadastro_sucesso @CAD-001
Funcionalidade: Cadastro de curso
  Cenário: Criar curso Online com dados válidos
    Dado que acesso "Cadastrar curso"
    Quando preencho todos os campos obrigatórios com dados válidos
      | Nome      | Testes Automatizados do Zero |
      | Descrição | Aprenda E2E                  |
      | Instrutor | Ana Silva                    |
      | URL       | https://ex.com/capa.jpg      |
      | Início    | 05/11/2025                   |
      | Fim       | 06/11/2025                   |
      | Vagas     | 30                           |
      | Tipo      | Online                       |
      | Link      | https://linkdeexemplo.com.br |
    E clico em "CADASTRAR CURSO"
    Então vejo mensagem de sucesso
    E o curso aparece na listagem
    E o curso persiste após recarregar a página

 ```

  ---
 ## US-002 — Validações de campos (gerais)
 **Como** operador
 **Quero** ser impedido de salvar dados inválidos
 **Para** manter integridade e qualidade do cadastro

 ```gherkin

@obrigatorios @CAD-002
Cenário: Bloquear envio com obrigatórios vazios
  Dado que acesso "Cadastrar curso"
  Quando deixo Nome, Instrutor, Tipo, Início, Fim e Vagas vazios
  E envio o formulário
  Então o envio é bloqueado
  E vejo mensagem de erro específica por campo

@min_caracteres @CAD-003
Cenário: Nome muito curto (<3)
  Dado que acesso "Cadastrar curso"
  Quando informo "AB" em Nome
  Então o envio é bloqueado com "mínimo 3 caracteres"

@espacos_em_branco @CAD-004
Cenário: Nome apenas com espaços
  Dado que acesso "Cadastrar curso"
  Quando informo "    " em Nome
  Então o envio é bloqueado com "valor inválido"

@descricao_curta @CAD-005
Cenário: Descrição muito curta
  Dado que acesso "Cadastrar curso"
  Quando informo "abc" em Descrição
  Então o envio é bloqueado com "descrição muito curta"

@instrutor_formato @CAD-006
Cenário: Instrutor com caracteres inválidos
  Dado que acesso "Cadastrar curso"
  Quando informo "1234" em Instrutor
  Então o envio é bloqueado com "formato inválido"

@url_invalida_esquema @CAD-007
Cenário: URL com esquema inválido (javascript:)
  Dado que acesso "Cadastrar curso"
  Quando informo URL "javascript:alert(1)"
  Então o envio é bloqueado com "Informe uma URL válida (http/https)"

@url_sem_protocolo @CAD-008
Cenário: URL sem protocolo
  Dado que acesso "Cadastrar curso"
  Quando informo URL sem http/https
  Então o envio é bloqueado com "Informe uma URL válida (http/https)"

@limites_texto @CAD-019
Cenário: Limites máximos ausentes nos campos de texto
  Dado que acesso "Cadastrar curso"
  Quando informo textos acima do limite (ex.: Nome=500 chars)
  Então o envio é bloqueado com "limite excedido"

@xss @CAD-017
Cenário: Prevenir XSS armazenado
  Dado que acesso "Cadastrar curso"
  Quando informo "<script>alert(1)</script>" em Nome e/ou Descrição
  Então o conteúdo deve ser exibido como texto literal (escapado)
  E nenhum script deve executar

```

---
## US-003 — Tipos Presencial/Online

Como operador
Quero que o formulário se adapte ao tipo
Para exigir Endereço (Presencial) e Link http/https (Online)

```gherkin

@presencial_endereco @CAD-026
Cenário: Tipo Presencial exige Endereço
  Dado que seleciono Tipo "Presencial"
  Quando Endereço está vazio ou inválido
  Então o envio é bloqueado com "Endereço é obrigatório"
  E o campo Link não deve ser obrigatório/visível

@online_link @CAD-027
Cenário: Tipo Online exige Link http/https
  Dado que seleciono Tipo "Online"
  Quando Link está vazio ou inválido (ftp://, javascript:, sem protocolo)
  Então o envio é bloqueado com "Informe um Link http/https válido"
  E o campo Endereço não deve ser obrigatório

@troca_tipo_limpa @CAD-028
Cenário: Troca de tipo limpa/valida campos do outro tipo
  Dado que preenchi Endereço em "Presencial"
  Quando troco o Tipo para "Online"
  Então o campo Endereço é limpo/ignorado
  E o formulário exige Link http/https

```

---
## US-004 — Datas do curso

Como operador
Quero regras claras para as datas
Para evitar inconsistências de agenda

```gherkin

@data_invalida @CAD-009
Cenário: Data com ano fora do intervalo
  Dado que acesso "Cadastrar curso"
  Quando informo "28/08/135133" em Data de início (ou fim)
  Então o envio é bloqueado com "Data inválida" (formato dd/mm/aaaa e faixa aceitável)

@fim_antes_inicio @CAD-010
Cenário: Data de fim anterior ao início
  Dado que acesso "Cadastrar curso"
  Quando informo Início=10/11/2025 e Fim=09/11/2025
  Então o envio é bloqueado com "Data de fim deve ser igual ou posterior à data de início"

@mesmo_dia
Cenário: Início e fim no mesmo dia
  Dado que acesso "Cadastrar curso"
  Quando informo Início=10/11/2025 e Fim=10/11/2025
  Então o envio é permitido

```

---
## US-005 — Listagem de cursos (UI/UX)

Como usuário da aplicação
Quero visualizar os cursos de forma consistente
Para facilitar leitura e navegação

```gherkin

@persistencia
Cenário: Persistência após recarregar
  Dado que acabo de cadastrar um curso
  Quando recarrego a página
  Então o curso permanece visível na listagem

@ui_cards @CAD-018 @CAD-022
Cenário: Consistência visual dos cards
  Dado que existem cursos com títulos/descrições curtos e longos
  Quando visualizo em 1440px, 768px e 360px de largura
  Então os cards permanecem alinhados por linha, sem "degraus"
  E não há rolagem horizontal

```

---
## US-006 — Excluir curso (funcional)

Como operador
Quero excluir um curso
Para removê-lo definitivamente

```gherkin

@excluir_sucesso @CAD-025
Cenário: Exclusão efetiva
  Dado um curso visível na listagem
  Quando clico em "Excluir"
  Então a aplicação envia DELETE para o recurso do curso
  E recebe 200 ou 204
  E remove o item da listagem
  E após recarregar a página o item não reaparece

```

---
## US-007 — Confirmação de exclusão (modal) — RFE
Status: RFE (não implementado)

```gherkin

@rfe_confirmacao @CAD-023
Cenário: Confirmar ou cancelar exclusão
  Dado um curso na listagem
  Quando clico em "Excluir"
  Então vejo um modal com "Tem certeza que deseja excluir?" e botões "SIM" e "NÃO"
  E ao clicar "NÃO" nada é removido
  E ao clicar "SIM" o item é removido definitivamente

```

[↑ Voltar ao topo](#topo)





