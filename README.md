# 🛠️ Princípios de Engenharia e Boas Práticas

Este documento serve como guia de referência para os princípios de design e arquitetura de código aplicados neste projeto.

---

## 🧠 Princípios Gerais

| SIGLA | **Aplicação (O que é)** | **Exemplo de Uso** |
| :---: | :--- | :--- |
| 💋 **KISS** | **Keep It Simple, Stupid**. Evite complexidade desnecessária. A solução mais simples geralmente é a melhor. | Usar um `if/else` claro em vez de importar uma biblioteca inteira ou usar *bitwise operations*. |
| ♻️ **DRY** | **Don't Repeat Yourself**. Evite duplicação de lógica. Cada conhecimento deve ter uma representação única. | Centralizar a lógica de `calcularImposto()` em uma função, em vez de repetir a fórmula em vários locais. |
| 🙅 **YAGNI** | **You Aren't Gonna Need It**. Não adicione funcionalidades pensando no "futuro incerto". Foque no agora. | Implementar apenas o `Login` solicitado na sprint, sem criar suporte para `OAuth` antecipadamente. |
| 🏕️ **Escoteiro** | **Boy Scout Rule**. Deixe o código mais limpo do que você o encontrou. | Ao corrigir um bug, aproveitar para renomear uma variável confusa ou apagar comentários mortos. |

---

## 💎 S.O.L.I.D. (Orientação a Objetos)

| **Emoji + Sigla** | **Princípio** | **Exemplo de Uso** |
| :---: | :--- | :--- |
| 🎯 **SRP** | **Single Responsibility**. Uma classe/função deve ter apenas *um* motivo para mudar. | Separar `UsuarioAuth` (login) de `UsuarioRepository` (banco) e `EmailService`. |
| 🔓 **OCP** | **Open/Closed**. Aberto para extensão, fechado para modificação. | Criar uma nova classe `PagamentoPix` que implementa uma interface, sem alterar o `ProcessadorPagamento`. |
| 🧩 **LSP** | **Liskov Substitution**. Subclasses devem poder substituir as classes pais sem quebrar o sistema. | Se `Pinguim` herda de `Ave`, ele não deve lançar erro ao chamar `voar()`. A abstração deve ser corrigida. |
| ✂️ **ISP** | **Interface Segregation**. Interfaces específicas são melhores que uma interface geral "faz-tudo". | Interfaces `IImpressora` e `IScanner` separadas, em vez de obrigar uma impressora simples a `escanear()`. |
| 🔌 **DIP** | **Dependency Inversion**. Dependa de abstrações, não de implementações concretas. | O *Service* depende de `IDatabase`, permitindo trocar de banco de dados ou usar um *Mock* de teste facilmente. |

---

## 💡 Dicas de Uso

1.  **Não seja dogmático:** O **KISS** (Simplicidade) deve equilibrar o **DRY** (Não repetição). Às vezes, duplicar 2 linhas de código é melhor do que criar uma abstração complexa demais.
2.  **Comece pelo 'S' (SRP):** A maioria dos problemas de código "sujo" se resolve apenas garantindo que cada função ou classe faça apenas uma coisa.
3.  **Refatore nos PRs:** Use o *Code Review* para apontar violações amigavelmente: *"Isso aqui viola o OCP, se adicionarmos outro status vamos ter que mudar esse arquivo de novo?"*
