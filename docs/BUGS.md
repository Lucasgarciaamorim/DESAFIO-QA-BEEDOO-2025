# Relatório de Bugs

> Evidências em vídeo vinculadas em cada linha.

| Bug ID | Título | Severidade | Status | Como reproduzir (resumo) | Casos relacionados | Evidência |
|---|---|---|---|---|---|---|
| BUG-001 | Obrigatórios sem validação | Crítico | Aberto | Deixar obrigatórios vazios e enviar | CAD-002, CAD-020 | [Vídeo](https://drive.google.com/file/d/10zgtOzYhfQ3x-P67rwpx7KpDjuyn8iYI/view?usp=drive_link) |
| BUG-006 | Validação de URL/esquema | Crítico | Aberto | URL `javascript:` / sem http/https aceita | CAD-007, CAD-008, CAD-027 | [Vídeo](https://drive.google.com/file/d/10yWAYaeDJ15MUiCoU3GF1UDbqgfrosLc/view?usp=drive_link) |
| BUG-007 | Quebra de Layout | Médio | Aberto | Cards com alturas distintas criam degraus | CAD-018, CAD-022 | [Vídeo](https://drive.google.com/file/d/1j4Gwb8ag-oRqgW9BmtbK_amdIlDrskKG/view?usp=drive_link) |
| BUG-008 | Ausência de limites de texto | Alto | Aberto | Campos aceitam 500+ caracteres | CAD-019 | [[Vídeo](https://drive.google.com/file/d/1di1bD_lcvt6v4_956pYiDVqTlzfgScIP/view?usp=drive_link) |
| BUG-010 | DELETE 405 (exclusão falha) | Crítico | Aberto | Ao excluir, Network 405 e item permanece | CAD-025 | [Vídeo](https://drive.google.com/file/d/1je6oVr7YJDBhEXvwacSY2K9WbPKQaVTo/view?usp=drive_link) |
| BUG-011 | XSS armazenado | Crítico | Aberto | `<script>` persistido/renderizado no card | CAD-017 | [Vídeo](https://drive.google.com/file/d/1oB2_eKakYYOLuT9InY5t6ZE3xYTA4vZ4/view?usp=drive_link) |
| BUG-012 | Fim < Início permitido | Alto | Aberto | Início=10/11; Fim=09/11 aceito | CAD-010 | [Vídeo](https://drive.google.com/file/d/1-wKvoMSsIGI1QD9i5m1hDqwT9Srmg1tQ/view?usp=drive_link) |
| BUG-015 | Tipo não obrigatório | Alto | Aberto | Salva sem definir Tipo | CAD-013 | [Vídeo](https://drive.google.com/file/d/1GCkhzz_OPg0QQx2rsbLGrHSA84YvqYQZ/view?usp=drive_link) |
| BUG-016 | Estado do CTA inválido | Médio | Aberto | Botão não desabilita com form inválido | CAD-015 | [Vídeo](https://drive.google.com/file/d/1DtRr4ayMLENCK4Cd1GDjRjPQn_EsZvEN/view?usp=drive_link) |
| BUG-018 | Presencial sem Endereço | Crítico | Aberto | Aceita Presencial sem endereço | CAD-026 | [Vídeo](https://drive.google.com/file/d/1ZXHmXXetbHEj8H1H6BasHkv0ZYu6j3GC/view?usp=drive_link) |
| BUG-019 | Online sem Link válido | Crítico | Aberto | Aceita Online sem http/https | CAD-027 | [Vídeo](https://drive.google.com/file/d/1Yze2g8PrinZsuBVDigjxXoUiJQr8TWNN/view?usp=drive_link) |
| BUG-020 | Data fora do intervalo | Alto | Aberto | Aceita `28/08/99999` | CAD-009 | [Vídeo](https://drive.google.com/file/d/1cjTQvaxTNsHmyO9qmxEi-Lzxk1lV-EzD/view?usp=drive_link) |


