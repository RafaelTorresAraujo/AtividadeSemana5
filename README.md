# Atividade Semana 5 – PDS
---

## 📂 Estrutura dos Arquivos
- `casos_de_uso.png` → Diagrama de Casos de Uso  
- `sequencia.png` → Diagrama de Sequência  
- `classes.png` → Diagrama de Classes  
 

---

## 👥 Diagrama de Casos de Uso
Mostra os **atores** (Membro, Administrador) e os principais **casos de uso**:
- Consultar catálogo de livros  
- Realizar empréstimo  
- Devolver livro  
- Cadastrar livros e membros  
- Gerar relatórios  

---

## 🔄 Diagrama de Sequência
Fluxo do **empréstimo de livro**:
1. Membro solicita empréstimo.  
2. Sistema verifica disponibilidade do livro.  
3. Sistema verifica pendências do membro.  
4. Se tudo ok, cria o empréstimo.  
5. Sistema confirma ao membro.  

---

## 🏗️ Diagrama de Classes
Classes principais:  
- **Livro** → armazena título, autor, exemplares, disponibilidade.  
- **Membro** → armazena dados do usuário, pendências e histórico.  
- **Empréstimo** → relaciona Livro + Membro, com datas e devolução.  
- **Administrador** → gerencia livros e membros.  

---


