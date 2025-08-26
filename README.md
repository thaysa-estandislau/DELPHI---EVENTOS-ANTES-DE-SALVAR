# 🏭 Validação de Locais de Estoque em Ordens de Produção (Delphi)

## 📌 Sobre o Projeto
Este projeto nasceu de uma necessidade real de negócio: **bloquear o salvamento de ordens de produção quando os produtos informarem locais de estoque não permitidos para determinado setor**.  

A primeira tentativa foi via **trigger no banco de dados**, mas a exceção não era exibida corretamente para o cliente.  
A solução definitiva veio com **Delphi**, validando os locais diretamente na tela antes de gravar a ordem de produção.  

---

## ⚙️ Como Funciona
1. A rotina percorre os **produtos acabados (PA)** e as **matérias-primas (MP)** da ordem de produção.  
2. Compara os locais informados com os locais **permitidos por setor** (armazenados na tabela `SETORES_U - Essa validação é feita através do setor em que o usuário digitou em tela`).  
3. Caso algum local seja inválido → a operação é bloqueada e o usuário recebe um alerta.  

📊 Os locais permitidos são parametrizados em:
- `LOCALPERMITIDOPA`: Locais permitidos para Produto Acabado  
- `LOCALPERMITIDOMP`: Locais permitidos para Matéria-Prima  

---

## 🛠️ Tecnologias e Conceitos Utilizados
- **Delphi**  
- **Banco de Dados** para pegar a lista de locais permitidos  
- **Validação preventiva em tela** antes de persistir no banco  

🔧 Estruturas usadas:
- `TClientDataSet` → consulta dos locais permitidos  
- `TStringList` → manipulação das listas de locais  
- `MessageDlg` → exibição de mensagens de alerta  
- `Abort` → cancelamento do salvamento quando houver inconsistência  

---

## 🔍 Exemplo de Validação
✔️ Se o local informado está na lista → ordem salva normalmente  
❌ Se o local informado não está na lista → operação bloqueada 
