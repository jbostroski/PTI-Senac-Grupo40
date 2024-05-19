<h1 align="center">Senac EAD - Análise e Desenvolvimento de Sistemas</h1>
<br>
<h2 align="center">Projeto Integrador: Desenvolvimento de Sistemas Orientado a Objetos.</h2>
<br>
Integrantes:
<br>
- Andrew Matos Ascar
<br>
- Humberto Moura Dos Anjos Junior
<br>
- Italo Da Silva Barbosa
<br>
- Jhonatan Bruno Ostroski


# Proposta do Projeto:

O projeto consiste no processo de modelagem de um sistema voltado a gestão de dados de um centro universitário **O projeto foi executado em duas etapas, listadas abaixo:**

## Primeira Entrega:

Desenvolvimento do diagrama de casos de uso representando os cenários referente ao sistema, composto pelas seguintes partes:

-   Pessoa Física;
-   Pessoa Jurídica;
-   Professores;
-   Fornecedores;
-   Alunos;

Descrição dos cenários dos casos de uso construídos, levando em consideração um cenário principal, dois cenários alternativos, pré-condições e pós-condições.

Previsto também a elaboração de um diagrama de classe, de acordo com a proposta do projeto; Foi utilizado a linguagem Mermaid, para representar os diagramas de classes UML e digrama de casos de uso.
<br>

Diagrama de Casos de Uso:
<br>
```mermaid
classDiagram
    class SistemaDeCadastroUniversitario {
        +validarLogin()
        +efetuarLogin()
        +acessarMenuDeCadastramento()
        +efetuarCadastro()
        +editarCadastro()
        +validacaoDoCadastro()
        +voltarAoMenuDeCadastros()
        +voltarATelaInicial()
    }

    class Usuario {
        <<abstract>>
        +login
        +senha
        +efetuarLogin()
        +validarLogin()
    }

    class PessoaFisica {
        +nome
        +cpf
        +dataDeNascimento
    }

    class PessoaJuridica {
        +razaoSocial
        +cnpj
        +dataDeFundacao
    }

    class Administrador {
        +acessarMenuDeCadastramento()
        +efetuarCadastro()
        +editarCadastro()
        +voltarAoMenuDeCadastros()
        +validacaoDoCadastro()
    }

    SistemaDeCadastroUniversitario --> Usuario : tem
    Usuario <|-- PessoaFisica
    Usuario <|-- PessoaJuridica
    SistemaDeCadastroUniversitario --> Administrador : tem

    class MenuDeCadastramento {
        +acessar()
        +voltarAoMenuDeCadastros()
    }

    class Cadastro {
        +efetuar()
        +editar()
        +validar()
    }

    Administrador --> MenuDeCadastramento
    Administrador --> Cadastro

```
<br>
Diagrama de Classe UML:
<br>

```mermaid
classDiagram
    class PessoaFisica {
        -id: Int
        -cpf: String
        +primeiroNome: String
        +sobrenome: String
        +dataNascimento: Date
        +dataCadastro: Date
        +telefone: Long
        +endereco: String
        -tipoPessoaFisica: Int
        +formacaoAcademica: String
        +habilitado: Bool
        +calculadade(dataNascimento): Int
        +desativarCadastro(habilitado): Void
    }

    class Aluno {
        -tipoPessoaFisica: Int
        +numeroMatricula: Int
        +dataMatricula: Date
        +aprovado: Bool
        +dataAprovacao: Date
        +aprovarAluno(aprovado): Void
        +matricular(pessoaFisicaId): Void
    }

    class Colaborador {
        -tipoPessoaFisica: Int
        -tipoCargo: Int
        +dataContratacao: Date
        +dataDesligamento: Date
        -tipoColaborador: Int
        #status: Int
        +cadastrarColaborador(pessoaFisicaId): Void
        +statusColaborador(pessoaFisicaId): String
    }

    class Professor {
        -tipoColaborador: Int
        +especializacao: String
        +agendarAula(pessoaFisicaId, materiaId, turmaId): Void
        +turmasCoordenadas(): String
    }

    class Cargos {
        -id: Int
        -tipoCargo: Int
        +setor: String
        +funcao: Int
    }

    class Materia {
        -id: Int
        +nome: String
        +segmento: String
        +area: String
        #dataCadastro: Date
        +modalidade: Int
        +valor: Float
        +descricao: String
        #cargaHoraria: Int
        +atualizarValor(valor): Void
    }

    class Turma {
        +professor: Professor
        +aluno: Aluno
        +materia: Materia
        #dataInicio: Date
        #dataFim: Date
        +disponibilidade: Bool
        #status: Int
        +indisponibilizarTurma(disponibilidade): Void
        +encerrarTurma(dataFim): Void
        +iniciarTurma(dataInicio): Void
    }

    PessoaFisica "1" -- "0..1" Aluno
    PessoaFisica "1" -- "0..1" Colaborador
    PessoaFisica "1" -- "0..1" Professor
    Colaborador "1" -- "0..1" Cargos
    Aluno "1..*" -- "1..*" Materia : Frequenta
    Turma "1..*" -- "1..1" Materia : Possui
    Turma "1..*" -- "1..*" Aluno : Possui
    Turma "1..1" -- "1..*" Professor : Leciona

```

## Segunda Entrega:

É composta pela prototipação (interface do sistema) do que foi realizado na primeira parte do projeto. Os protótipos contemplam as seguintes interfaces:

[Cadastro de Pessoa Física](https://github.com/jbostroski/PTI-Senac-Grupo40/blob/main/pessoa_fisica.png)
<br>
[Cadastro de Pessoa Jurídica](https://github.com/jbostroski/PTI-Senac-Grupo40/blob/main/pessoa_juridica.png)
<br>
[Cadastro de Professores](https://github.com/jbostroski/PTI-Senac-Grupo40/blob/main/professor.png)
<br>
[Cadastro de Fornecedores](https://github.com/jbostroski/PTI-Senac-Grupo40/blob/main/fornecedores.png)
<br>
[Cadastro de Alunos](https://github.com/jbostroski/PTI-Senac-Grupo40/blob/main/alunos.png)


Os protótipos foram desenvolvidos utilizando a ferramenta Figma. 

**Os arquivos foram reunidos neste repositório.**
