# Avaliação 26/10/2026 — idioma e fórmulas

## 1. Diálogo ao fechar
Em `crates/ui-egui/src/dialogs.rs`, o caso `saveChanges` traduz apenas o título. Traduzir também a pergunta "Do you want to save the changes you made to {}?" e botões "Don't Save", "Cancel" e "Save" para "Deseja salvar as alterações feitas em {}?", "Não salvar", "Cancelar" e "Salvar" quando `Language::PtBr`. Usar catálogo i18n para não duplicar textos, testar salvar, descartar e cancelar.

## 2. Formato contábil
Em `crates/ui-egui/src/ribbon.rs`, a lista `ACCOUNTING_SYMBOLS` já contém "R$ Portuguese (Brazil)" com código `[$R$-416]`. Na interface pt-BR, priorizar "R$ — Português (Brasil)" e fazer o clique principal de `home.accounting` aplicar a configuração brasileira (2 casas e separadores corretos); preservar seleção explícita e outros idiomas. Testar ida/volta XLSX.

## 3. AutoSoma e operações
No vídeo Excel inicia edição de `=SOMA(...)` e destaca as células para ajuste antes da confirmação. Atualmente o clique principal `formulas.autoSum` executa diretamente. Mudar UX para propor fórmula editável com intervalo selecionável, confirmação por Enter e cancelamento por Esc, sem alterar diretamente o documento até confirmar. O submenu em `autosum_menu` já lista SUM/AVERAGE/COUNT/MAX/MIN; traduzir para Soma, Média, Contagem, Máximo, Mínimo. Multiplicação (*) e divisão (/) não são opções nativas do Excel AutoSoma; especificar adicional próprio com seleção de operandos e testes, sem tratar como operações de AutoSoma.

## Aceite
Testes automatizados da tradução, formato monetário e fórmulas, build Windows x64, conferência visual e validação de criar/abrir/editar/salvar. Não distribuir versão de clientes sem testes.
