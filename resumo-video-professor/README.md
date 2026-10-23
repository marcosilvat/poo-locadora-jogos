# Resumo do Vídeo do Prof. José Antônio (`POO_Erros_Comuns_Entrega_Projeto_Pessoal.mp4`)

Ele mostra na tela exatamente como corrige os trabalhos (abrindo o diagrama de classes ao lado dos arquivos `.java`) e passa um **checklist oficial** dos erros que mais descontaram nota (ou anularam entregas).

---

## 1. Regras de Envio (`03:08` – `05:43`)
- **Arquivo único compactado (`.zip`)**: Enviar todos os `.java` + a imagem do Diagrama de Classes dentro de **um único arquivo compactado**.
- **Proibido enviar `.class` (bytecodes)**: Enviar **somente** os arquivos `.java` e o diagrama.
- **Formato do Diagrama de Classes**: Exportar obrigatoriamente em **`.png`, `.bmp` ou `.pdf`** (nunca enviar apenas o arquivo `.asta` do Astah ou de outra ferramenta).

## 2. Regras de Projeto, Diagrama e Código (`05:44` – `16:42`)
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

---

## Proposta de Modelagem para a Locadora de Jogos (Seguindo 100% do Vídeo)

Para atender ao tema (**Locadora de Jogos Eletrônicos** com arrays de clientes, atendentes, jogos e locações, e multa por atraso variando por tipo de jogo) e cumprir **todos** os critérios do Prof. José Antônio:

1. **Hierarquia 1 — `Pessoa` (`abstract class`)**:
   - Atributos privados em `Pessoa`: `codigo`, `nome`, `cpf`, `telefone` + composição com `Endereco` (`rua`, `numero`, `cidade`).
   - Filha 1 — **`Cliente extends Pessoa`**: atributos próprios `email`, `categoriaFidelidade`, `limiteJogosAtivos`. (*Cliente é um tipo de Pessoa? Sim!*)
   - Filha 2 — **`Atendente extends Pessoa`**: atributos próprios `matricula`, `turno`, `comissaoPorLocacao`. (*Atendente é um tipo de Pessoa? Sim!*)
2. **Hierarquia 2 — `Jogo` (`abstract class` implementando a interface `Calculavel`)**:
   - Atributos privados em `Jogo`: `codigo`, `titulo`, `genero`, `plataforma`, `valorDiaria`.
   - Método abstrato/interface: `calcularMultaPorDia()` (polimorfismo!).
   - Filha 1 — **`JogoMidiaFisica extends Jogo`**: atributos próprios `codigoMidia`, `estadoConservacao`, `taxaReposicaoCaixa` (multa maior por dia de atraso).
   - Filha 2 — **`JogoDigital extends Jogo`**: atributos próprios `chaveLicenca`, `tamanhoGb`, `horasExpiracaoToken` (multa diferenciada por dia de atraso).
3. **Classe Associativa / Composição — `Locacao` (implementando `Calculavel`)**:
   - Composta por: `Cliente cliente`, `Atendente atendente`, `Jogo jogo`, além de `codigoLocacao`, `diasPrevistos`, `diasAtraso`.
   - Calcula o valor total polimorficamente somando `(diasPrevistos * jogo.getValorDiaria()) + (diasAtraso * jogo.calcularMultaPorDia())`.
4. **Classe de Serviço — `Leitura`**:
   - Método `entDados(String rotulo)` separado da classe `main` (alta coesão, como o professor pediu).
5. **Classe Única de Teste — `Principal` (ou `TstLocadora`)**:
   - Possui o único `public static void main(String[] args)` com os arrays (`Cliente[]`, `Atendente[]`, `Jogo[]`, `Locacao[]`) e um menu interativo via teclado que cadastra, lista e testa todas as classes!
