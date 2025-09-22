#  Atividade – Semana 5 (PDS)

## Parte 1 – Diagrama de Casos de Uso

**Atores:**  
- Membro do Clube  
- Administrador (ou Biblioteca)  

**Casos de Uso principais:**  
- Consultar catálogo de livros  
- Verificar disponibilidade de livro  
- Realizar empréstimo de livro  
- Devolver livro  
- Cadastrar novo livro  
- Atualizar dados de livro  
- Cadastrar novo membro  
- Atualizar dados de membro  
- Verificar histórico de empréstimos  
- Gerar relatórios de livros mais populares  

---

## Parte 2 – Diagrama de Sequência (Realizar Empréstimo – Fluxo de Sucesso)

**Fluxo resumido:**  
1. Membro solicita empréstimo.  
2. Tela de Empréstimo recebe dados (ID do membro e ID do livro).  
3. Controlador de Empréstimo verifica disponibilidade do livro.  
4. Livro retorna se está disponível.  
5. Controlador de Empréstimo verifica pendências do membro.  
6. Se não houver problemas, cria um objeto Empréstimo.  
7. Repositório salva o empréstimo.  
8. Tela confirma ao membro o sucesso da operação.  

**Mensagens principais:**  
- `Membro -> TelaDeEmprestimo: solicitarEmpréstimo()`  
- `TelaDeEmprestimo -> ControladorDeEmprestimo: enviarDados(membroID, livroID)`  
- `ControladorDeEmprestimo -> Livro: verificarDisponibilidade(livroID)`  
- `Livro -> ControladorDeEmprestimo: disponibilidade(sim/não)`  
- `ControladorDeEmprestimo -> Membro: verificarPendencias(membroID)`  
- `Membro -> ControladorDeEmprestimo: pendencias(ok/problema)`  
- `ControladorDeEmprestimo -> Empréstimo: criar(membro, livro, data)`  
- `Empréstimo -> Repositório: salvar(empréstimo)`  
- `ControladorDeEmprestimo -> Tela: exibirConfirmação()`  

---

## Parte 3 – Diagrama de Classes

**Classes e responsabilidades:**  

###  Livro
- Atributos: id, título, autor, anoPublicacao, editora, numeroExemplares, numeroDisponiveis  
- Métodos: verificarDisponibilidade(), incrementarExemplares(n), decrementarDisponiveis()  

###  Membro
- Atributos: id, nome, email, telefone, dataCadastro, status, multa (opcional)  
- Métodos: temPendencias(), notificarAtraso()  

###  Empréstimo
- Atributos: id, dataEmprestimo, dataDevolucaoPrevista, dataDevolucaoReal, livro, membro  
- Métodos: calcularAtraso(), estaAtrasado(), marcarDevolucao(data)  

###  Administrador
- Atributos: id, nome, senha, permissao  
- Métodos: cadastrarLivro(), atualizarLivro(), removerLivro(), cadastrarMembro(), gerarRelatorios()  

**Relacionamentos:**  
- Um **Membro** pode ter vários (0..*) **Empréstimos**.  
- Um **Livro** pode estar em vários (0..*) **Empréstimos**.  
- Um **Empréstimo** sempre relaciona **1 Membro** com **1 Livro**.  
- O **Administrador** gerencia livros e membros.  
