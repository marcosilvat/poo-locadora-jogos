# Resumo do Vídeo e Regras Oficiais — POO (Prof. José Antônio)

Este documento reúne o checklist extraído do vídeo (`POO_Erros_Comuns_Entrega_Projeto_Pessoal.mp4`) e as **9 regras oficiais do enunciado**.

---

## Parte 1 — As 9 Regras Oficiais da Instrução

1. **Compilação e Funcionamento**: Antes de enviar, tenha certeza de que sua aplicação está compilando e funcionando de acordo com as solicitações feitas nos enunciados. Não serão aceitas aplicações que não atendam estas recomendações.
2. **Conceitos de POO**: Sempre atente para que a aplicação contenha os conceitos e técnicas da Programação Orientada a Objetos vistos até o momento do envio e explicitados nos enunciados (encapsulamento, herança, classes abstratas, polimorfismo, interface, composição, reflexividade).
3. **Sem Banco de Dados (SGBD)**: O projeto **NÃO** pede uso de SGBD (MySQL, SQL Server, Oracle, PostgreSQL, etc.) — **NÃO USE** (armazenamento em arrays em memória).
4. **Entidades Físicas do Mundo Real**: O projeto deve tratar da gestão de entidades (coisas ou pessoas) que existam **fisicamente no mundo real** (excluem-se roteiros, regras de um jogo em si ou itens puramente virtuais; na locadora, todas as classes devem representar pessoas e mídias/itens físicos reais, como Mídia Óptica/Blu-Ray, Cartucho e Edição de Colecionador).
5. **Sem Validação de CPF ou Senha/Login**: **NÃO** utilize sistemas de validação para documentos (ex.: cálculo verificador de CPF) nem telas de usuário/senha (para não travar o teste rápido do professor quando ele digitar valores curtos como `1` ou `abc`).
6. **Apenas arquivos `.java`**: Envie apenas os códigos-fontes (`.java`), nunca `.class` (bytecodes).
7. **Formato do Diagrama de Classes**: Deve estar em formato popular: **PDF ou PNG** (ou BMP).
8. **IDE (NetBeans ou `.java` puros)**: Se for enviar estrutura de projeto de IDE, que seja exclusivamente **NetBeans** (ou apenas os arquivos `.java` + diagrama compactados).
9. **Cabeçalho Obrigatório em TODOS os `.java`**: Colocar de forma comentada o **RA e Nome Completo** nas primeiras linhas de **TODOS** os arquivos `.java`:
   ```java
   // Nome: Marco Antonio Teodoro da Silva
   // RA: <SEU_RA_AQUI>
   ```

---

## Parte 2 — Checklist do Vídeo (`POO_Erros_Comuns_Entrega_Projeto_Pessoal.mp4`)

### 1. Regras de Envio (`03:08` – `05:43`)
- **Arquivo único compactado (`.zip`)**: Enviar todos os `.java` + a imagem do Diagrama de Classes dentro de **um único arquivo compactado**.
- **Proibido enviar `.class` (bytecodes)**: Enviar **somente** os arquivos `.java` e o diagrama.
- **Formato do Diagrama de Classes**: Exportar obrigatoriamente em **`.png`, `.bmp` ou `.pdf`**.

### 2. Regras de Projeto, Diagrama e Código (`05:44` – `16:42`)
1. **Espelhamento 100% entre Diagrama e Código (`07:38` – `08:22`)**:
   - A quantidade de classes, os nomes das classes, os nomes/tipos dos atributos e os métodos no código `.java` precisam ser **idênticos** aos do diagrama, incluindo as setas de associação, composição e herança.
2. **Convenção de Nomes (`10:35` e `11:34`)**:
   - **Classes**: sempre começam com **Letra Maiúscula** (`Cliente`, `Atendente`, `Jogo`, `Locacao`, `Leitura`).
   - **Atributos e Métodos**: sempre começam com **letra minúscula** (`calcularMulta()`, `diasAtraso`, `entDados()`), tanto no código quanto no diagrama.
3. **Coesão e Entrada de Dados via Teclado (`06:51`, `10:50`, `15:08`)**:
   - **Obrigatório ler dados via teclado** (não passar valores fixos direto nos `setters`).
   - **Alta coesão**: **Não** colocar o método de leitura de teclado dentro da classe que tem o `main`. Criar uma classe separada dedicada à leitura (ex.: `Leitura` com `entDados(String rotulo)`).
4. **Herança Real ("É um tipo de...") com 2+ classes-filhas e 2+ atributos próprios (`11:55` – `15:00`)**:
   - A relação precisa responder **"SIM"** à pergunta: *"ClasseFilha **é um tipo de** ClasseMãe?"*.
   - **Proibido herança com apenas 1 classe-filha**: toda classe-mãe precisa ter **pelo menos 2 ou 3 classes-filhas**.
   - **Cada classe-filha precisa ter mais de 1 atributo próprio** (além dos herdados da mãe) para justificar o uso da herança.
5. **Encapsulamento, Construtores e Reflexividade (`15:01` – `15:43`)**:
   - Nas classes de entidade, **todos os atributos devem ser `private`** (`-` no diagrama) e os `getters`/`setters` **`public`** (`+` no diagrama).
   - Todas as classes devem ter **métodos construtores** (padrão e sobrecarregado).
   - **Reflexividade**: usar `this.` e `super.` / `super(...)` nas classes-filhas para reaproveitar construtores e métodos da classe-mãe.
6. **Apenas UMA classe com `main` que testa TUDO (`08:28`, `15:44` – `16:35`)**:
   - **Proibido** ter `main` em mais de uma classe.
   - Deve existir **uma única classe principal** (ex.: `Principal` ou `TstLocadora`) que instancia e testa **todas** as classes-filhas e funcionalidades do sistema.
