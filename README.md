# Delivery de Bebidas - MAF (Mínimo Aplicativo Funcional)

Aplicativo Android de **delivery de bebidas**, desenvolvido em **Kotlin + Jetpack Compose** para a disciplina de **Desenvolvimento de Aplicativos Móveis**.

Este repositório é a **terceira parte do Trabalho** da A2 e dá continuação ao Trabalho 2. Aqui o app passou a guardar os dados em um banco de dados real.

---

## Objetivos

* Desenvolver uma aplicação mobile funcional, em que os dados persistem mesmo após fechar o app;
* Documentar o processo e as decisões do trio.

---

## Figma (Trabalho 1)

Board com a UI das 5 telas originais do Trabalho 1:

* Tela de Início
* Tela do Produto
* Tela do Carrinho
* Tela do Pagamento
* Tela de Verificação (rastreio) do pedido

https://www.figma.com/design/FGavv6Oe5wV3DbMC6QftjL/atividade-android?node-id=0-1&t=4b5kjobzLUZ87pgu-1

---

## Canvas: por que esse aplicativo existe?

**Qual problema esse aplicativo resolve? Para quem ele é?**

O app resolve o problema de comprar bebida em cima da hora, quando o usuário já decidiu o que quer e precisa que chegue rápido, sem ter que sair de casa ou ir a um mercado físico.

**Por que alguém abriria esse aplicativo hoje? E por que abriria de novo amanhã?**

Hoje, abriria porque percebeu que está faltando bebida para um evento próximo e precisa resolver rápido. Abriria de novo amanhã se a experiência de pedir tiver sido simples e rápida da primeira vez.

**Qual é a única coisa que o aplicativo precisa fazer bem para "funcionar" na cabeça de quem usa?**

Dar confiança de que o pedido vai chegar rápido e no lugar certo.

**Se fosse um produto de verdade, como ele geraria valor ou dinheiro?**

De forma hipotética, por comissão sobre cada pedido repassada aos estabelecimentos parceiros, por taxa de entrega no checkout, e por destaque pago de produtos, um espaço que fornecedores poderiam pagar para aparecer, parecido com o modelo de outros apps de delivery.

**Quais decisões de tela vieram dessas respostas?**

Por isso a tela inicial mostra a categoria e os produtos mais pedidos: o usuário já sabe o que quer, então a prioridade é reduzir cliques até o carrinho, não apresentar o app. Pelo mesmo motivo, a tela de rastreio expõe o tempo estimado de chegada em destaque em vez de detalhes menos urgentes como o histórico completo do pedido.

---

## O que o app faz

* **Início:** categorias em carrossel, banner de frete grátis, "Mais pedidos por aqui" e "Ofertas da Semana" (produtos com desconto). Dá para abrir um produto ou adicioná-lo direto ao carrinho pelo botão **+**.
* **Produtos (lista):** todos os produtos cadastrados. É possível **adicionar** (botão flutuante), **editar**, **remover** (com diálogo de confirmação) e **abrir** o detalhe.
* **Categorias (lista):** todas as categorias, com a quantidade de produtos de cada uma. Também permite **adicionar**, **editar**, **remover** e **abrir** os produtos daquela categoria.
* **Carrinho:** altera a quantidade (e remove ao chegar em zero), calcula subtotal, taxa de entrega e total, e leva ao pagamento.
* **Pagamento → Rastreio:** escolha da forma de pagamento, resumo calculado a partir do carrinho e acompanhamento do pedido.

---

## Mapa de telas e navegação

O app tem **10 telas**, todas registradas em um único `NavHost` (`navegacao/AppNavigation.kt`).

| # | Tela | Rota | Função |
|---|------|------|--------|
| 1 | Início | `home` | Vitrine: categorias, mais pedidos e ofertas |
| 2 | **Lista de Produtos** | `produtos` | Lista + adicionar / editar / remover |
| 3 | **Detalhes do Produto** | `produto/{id}` | Imagem, dados, seletor de quantidade e total calculado |
| 4 | Formulário de Produto | `formProduto/{id}` | Cria (`id = -1`) ou edita um produto |
| 5 | **Lista de Categorias** | `categorias` | Lista + adicionar / editar / remover |
| 6 | **Detalhes da Categoria** | `produtosPorCategoria/{id}` | Produtos pertencentes àquela categoria |
| 7 | Formulário de Categoria | `formCategoria/{id}` | Cria ou edita uma categoria |
| 8 | Carrinho | `carrinho` | Itens, quantidades e resumo do pedido |
| 9 | Pagamento | `pagamento` | Forma de pagamento e confirmação |
| 10 | Rastreio | `rastreio` | Status e tempo estimado do pedido |

A **barra inferior** (`NavigationBar`) leva a **Início, Carrinho, Pedidos (Rastreio) e Produtos** em qualquer tela principal.

---



## Tecnologias utilizadas

* **Linguagem:** Kotlin
* **IDE:** Android Studio
* **Plataforma:** Android
* **Interface:** Jetpack Compose (Material 3)

```
## Como executar

### Pré-requisitos

* [Android Studio](https://developer.android.com/studio)
* Android SDK compatível com o projeto
* JDK compatível com a versão utilizada pelo projeto

### Passo a passo

1. Clone este repositório:

```bash
git clone <URL_DO_REPOSITORIO>
```

2. Abra o projeto no **Android Studio**.
3. Aguarde o Gradle sincronizar e baixar as dependências.
4. Conecte um dispositivo Android ou inicie um emulador.
5. Clique em **Run ▶**.

### Roteiro rápido de teste (o mesmo da apresentação)

1. Na barra inferior, abra **Produtos** → toque no **+** → cadastre um produto → ele aparece na lista.
2. Toque na **lixeira** de um produto → confirme → ele some da lista.
3. Toque em um produto (fora dos ícones) → confira que os **detalhes são do item tocado** → mude a quantidade e veja o total mudar → **Adicionar ao carrinho**.
4. Abra **Início → Gerenciar** (Categorias) → adicione, edite e remova uma categoria.
5. Toque em uma categoria → veja somente os produtos dela.
6. No **Carrinho**, altere quantidades → **Ir para pagamento** → **Confirmar pedido** → veja o **Rastreio**.
7. Navegue por todas as abas da barra inferior e use o botão de voltar.

---

## Anexos

https://drive.google.com/drive/folders/1D5RiLn466mixH6bFV3fAX9WgHVDCdutl?usp=sharing

---

## Licença

Este projeto foi desenvolvido para fins acadêmicos e não possui finalidade comercial.