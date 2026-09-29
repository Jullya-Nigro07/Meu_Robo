# Gerador de Relátorios com BOT 🤖

Robô de automação desenvolvido em Python para coletar dados, gerar relatórios em CSV e automatizar sua execução utilizando GitHub Actions.

O projeto demonstra como automatizar uma tarefa com Python e configurar um workflow para executar o processo periodicamente, registrando as alterações do relatório diretamente no repositório Git.

## 🎯 Objetivo do projeto

Este projeto foi desenvolvido para praticar automação de tarefas com Python e integração contínua por meio do GitHub Actions.

A aplicação reúne conceitos de manipulação de dados, geração de arquivos CSV, execução agendada de scripts e automação de operações Git em um workflow.

## Funcionalidades

- Coleta de dados utilizando Python.
- Registro da data, do evento e do status do processamento.
- Organização dos dados com a biblioteca Pandas.
- Geração automática de relatórios no formato CSV.
- Execução agendada por meio do GitHub Actions.
- Execução manual do workflow pela interface do GitHub.
- Versionamento automático das alterações no relatório gerado.

## ⚙️ Como funciona

O processo de automação segue estas etapas:

- O GitHub Actions inicia o workflow conforme o agendamento configurado ou por acionamento manual.
- O repositório é disponibilizado no ambiente de execução.
- As dependências do projeto são instaladas.
- O script bot.py é executado.
- Os dados coletados são organizados utilizando Pandas.
- O relatório relatorio.csv é gerado na pasta dados/.
- O workflow verifica as alterações e tenta criar um commit.
- Caso existam alterações e as permissões estejam configuradas corretamente, o relatório é enviado ao repositório.

## 🛠️ Instalação e execução local
1. Clone o repositório
```bash
git clone https://github.com/Jullya-Nigro07/GeradorDeRelatorios.git
```
2. Instale as dependências
```bash
pip install -r requirements.txt
```

3. Execute o robô
```bash
python bot.py
```

🗂️ Após a execução, o relatório será salvo em  ➔  dados/relatorio.csv

O terminal exibirá uma mensagem informando que o relatório foi salvo com sucesso.

## 📊 Exemplo do relatório

O arquivo CSV gerado contém as seguintes colunas:

#
| data | evento | status |
|---|---|---|
| Data da execução | Processamento finalizado | OK |

#


A data é obtida durante a execução do script, enquanto o evento e o status representam as informações registradas pelo processo de automação.

## ⏰ Automação com GitHub Actions

O workflow está definido em ➔ .github/workflows/automacao.yml

Atualmente, ele possui dois modos de execução:

- Agendado: diariamente às 08h UTC, equivalente às 05h no horário de Brasília quando aplicável.
- Manual: por meio da opção Run workflow na aba Actions do repositório.

O agendamento é configurado com a expressão cron:
```bash
on:
  schedule:
    - cron: '0 8 * * *'
  workflow_dispatch:
```

O workflow também contém etapas para configurar a identidade do Git, registrar as alterações do relatório e executar o git push.

🚨 Importante: para que o GitHub Actions consiga enviar alterações ao repositório, o workflow precisa ter permissão de escrita no conteúdo do repositório. Isso pode ser configurado em Settings → Actions → General → Workflow permissions, selecionando a opção de leitura e escrita (Read and write permissions).

---
