# 🦺 n8n · Gestão de Ocorrências de Segurança (Pirâmide de Heinrich)

Workflow em **n8n** que automatiza a gestão de ocorrências de segurança do trabalho usando a **Pirâmide de Heinrich** (atos inseguros → quase-acidentes → acidentes leves → acidentes graves).

Em vez de alguém ler a planilha, classificar cada ocorrência e montar o relatório na mão, o fluxo faz tudo sozinho e entrega o resultado por e-mail.

## ⚙️ Como funciona

```
Google Sheets ──► Agente de IA ──► Template HTML ──► Gmail
 (ocorrências)    (classifica no     (relatório       (envio aos
                   nível da pirâmide) formatado)       responsáveis)
```

1. **Gatilho**: lê as novas ocorrências registradas na planilha do Google Sheets.
2. **Agente de IA**: analisa a descrição e classifica cada ocorrência no nível correspondente da Pirâmide de Heinrich.
3. **Code node (JavaScript)**: agrupa os dados e calcula os totais por nível.
4. **Template HTML**: gera um relatório visual com a pirâmide e a lista de ocorrências.
5. **Gmail**: envia o relatório aos responsáveis pela segurança.

## 🧰 Tecnologias

- n8n
- JavaScript (Code node)
- Google Sheets API
- Gmail API
- Agente de IA (LLM)
- HTML/CSS

## ▶️ Como usar

1. Tenha uma instância do n8n rodando (n8n Cloud ou `npx n8n` / Docker).
2. No n8n, vá em **Workflows → Import from File** e importe o arquivo `workflow.json` deste repositório.
3. Configure as credenciais:
   - **Google Sheets** e **Gmail** (OAuth2 da sua conta Google)
   - **Modelo de IA** (chave de API do provedor usado no node do agente)
4. No node do Google Sheets, aponte para a sua planilha. Colunas esperadas: `data`, `setor`, `descricao`, `responsavel`.
5. No node do Gmail, defina os destinatários.
6. Clique em **Execute Workflow** para testar e depois ative o fluxo.

## 📸 Prints

> Adicione aqui um print do workflow no editor do n8n e um do e-mail gerado.

## 📚 Aprendizados

- Estruturar um fluxo de ponta a ponta com integração entre várias APIs
- Usar IA para classificar texto livre de forma padronizada
- Diagnosticar e corrigir erros de configuração e arquitetura ao longo das versões

## 👤 Autor

**Paulo Henrique Marques** · [GitHub](https://github.com/pmw17) · paulohenriquemarques29@gmail.com
