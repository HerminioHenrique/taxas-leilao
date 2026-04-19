# 🔨 Calculadora de Taxas de Leilão ASM / ASM Auction Fee Calculator

> 🇧🇷 Português abaixo · 🇬🇧 English below

---

## 🇧🇷 Português (Brasil)

### Sobre o Projeto

Uma calculadora web de **arquivo único** criada para calcular automaticamente o custo total de arrematação de veículos nos leilões da **ASM** no Reino Unido. 

O site da ASM não oferece nenhuma ferramenta de cálculo integrada, tornando necessário somar manualmente o lance, a Buyer's Fee, o VAT e as taxas extras durante um leilão ao vivo — o que consome tempo e aumenta o risco de erros. Esta calculadora foi feita para resolver exatamente esse problema, permitindo obter o **custo total final em segundos**.

---

### ❓ Por que esta ferramenta existe

Leilões de veículos da ASM cobram múltiplas taxas além do valor do lance (hammer price):

- **Buyer's Fee** — taxa escalonada por faixa de preço (tabela diferente para cada tipo de leilão)
- **VAT (20%)** — imposto aplicado sobre a Buyer's Fee (no leilão padrão)
- **Taxa extra do lote** — cobrada por alguns lotes específicos, com VAT de 20% em cima
- **Taxa fixa administrativa** — £35 + 20% VAT = £42.00 (somente no leilão padrão)

Somar tudo isso na cabeça durante um leilão ao vivo, com lances subindo a cada segundo, é inviável. A calculadora faz isso instantaneamente.

---

### ✨ Funcionalidades

#### 🏷️ Dois Tipos de Leilão

**Leilão Padrão**
- Buyer's Fee por faixa de valor (tabela com 23 faixas, de £0 a £11.999)
- Para lances acima de £12.000: Buyer's Fee = 6% do lance + 20% VAT (total de 7,2%)
- VAT de 20% sobre a Buyer's Fee
- Taxa extra do lote (opcional) + 20% VAT
- Taxa fixa de £35 + VAT = **£42.00**

**Police Auction (Leilão Policial)**
- Estrutura de taxas diferente, com 14 faixas de valor (de £0 a £14.999)
- Para lances acima de £15.000: Buyer's Fee = 6% do lance
- Fees são declaradas **ex-VAT** (sem VAT sobre a Buyer's Fee)
- Taxa extra do lote (se houver) ainda recebe 20% de VAT
- **Sem** taxa fixa administrativa

#### 🎯 Dois Modos de Cálculo

**Modo Direto (Forward)**
- Você informa o **valor do lance** e a calculadora mostra o custo total detalhado
- Exibe cada componente separadamente: lance, Buyer's Fee, VAT, taxa extra, taxa fixa e total
- Atualização em tempo real conforme você digita

**Modo Reverso (Reverse)**
- Você informa o **total máximo que deseja gastar** e a calculadora encontra o lance máximo que não ultrapassa esse valor
- Exibe o **"Lance Recomendado"** — o valor exato máximo que você pode dar no leilão
- Ideal para quem tem um orçamento definido e precisa saber até onde pode ir
- O cálculo é feito por busca iterativa com precisão de £0,01

#### 📋 Tabelas de Referência
- Tabela completa de faixas de taxas para o **Leilão Padrão** (com Buyer's Fee, VAT e total)
- Tabela completa de faixas para o **Police Auction**
- As tabelas mudam automaticamente conforme o tipo de leilão selecionado

---

### 🧮 Lógica de Cálculo

**Leilão Padrão — Modo Direto:**
```
Total = Lance + Buyer's Fee + (Buyer's Fee × 20%) + Taxa Extra + (Taxa Extra × 20%) + £42.00
```

**Police Auction — Modo Direto:**
```
Total = Lance + Buyer's Fee (ex-VAT) + Taxa Extra + (Taxa Extra × 20%)
```

**Modo Reverso:**
A calculadora itera de £0,01 até o valor restante após descontar taxas fixas, testando cada lance possível até encontrar o maior valor cujo total não ultrapasse o orçamento informado.

**Buyer's Fee acima dos limites de tabela:**
- Leilão Padrão: lances ≥ £12.000 → Buyer's Fee = 6% do lance
- Police Auction: lances ≥ £15.000 → Buyer's Fee = 6% do lance

---

### 🚀 Como Usar

Não há instalação. O app é um **único arquivo HTML** sem dependências externas.

1. Baixe ou clone o repositório
2. Abra o arquivo `index.html` no navegador — funciona offline, sem internet
3. Selecione o tipo de leilão (**Padrão** ou **Police Auction**)
4. Escolha o modo de cálculo:
   - **Modo Direto**: informe o valor do lance → veja o total
   - **Modo Reverso**: informe o seu orçamento máximo → veja o lance máximo
5. Se houver taxa extra no lote, insira-a no campo correspondente

> 💡 **Dica de uso em leilão ao vivo:** Use o Modo Reverso com o seu orçamento já preenchido. Assim, ao surgir um lote interessante, você já sabe imediatamente até qual valor pode dar o lance.

---

### 🛠️ Tecnologias

Propositalmente simples — zero dependências, zero instalação.

| Tecnologia | Uso |
|---|---|
| HTML5 | Estrutura da página |
| CSS3 | Estilização (sem frameworks) |
| JavaScript Vanilla | Toda a lógica de cálculo |

---

### ⚠️ Aviso

As tabelas de taxas foram baseadas nas estruturas de cobrança da ASM em vigor no momento da criação desta ferramenta. As taxas podem ser atualizadas pela ASM sem aviso prévio. Sempre confirme os valores finais com a tabela oficial do site da ASM antes de arrematar.

---

---

## 🇬🇧 English

### About the Project

A single-file web **calculator** built to automatically compute the total cost of buying vehicles at **ASM auctions** in the United Kingdom.

The ASM website offers no built-in fee calculation tool, making it necessary to manually add up the hammer price, Buyer's Fee, VAT, and any extra lot fees during a live auction — which is time-consuming and error-prone. This calculator was built to solve exactly that problem, giving you the **full final cost in seconds**.

---

### ❓ Why This Tool Exists

ASM vehicle auctions charge multiple fees on top of the hammer price:

- **Buyer's Fee** — a tiered fee based on price range (different tables for each auction type)
- **VAT (20%)** — applied on top of the Buyer's Fee (standard auction only)
- **Extra lot fee** — charged on specific lots, with 20% VAT applied on top
- **Fixed admin fee** — £35 + 20% VAT = £42.00 (standard auction only)

Adding all of this up mentally during a live auction, with bids rising by the second, is not practical. This calculator does it instantly.

---

### ✨ Features

#### 🏷️ Two Auction Types

**Standard Auction**
- Tiered Buyer's Fee by price range (23 tiers from £0 to £11,999)
- Bids above £12,000: Buyer's Fee = 6% of hammer price + 20% VAT (effective rate: 7.2%)
- 20% VAT on Buyer's Fee
- Optional extra lot fee + 20% VAT
- Fixed admin fee of £35 + VAT = **£42.00**

**Police Auction**
- Different fee structure with 14 tiers (from £0 to £14,999)
- Bids above £15,000: Buyer's Fee = 6% of hammer price
- Fees are quoted **ex-VAT** (no VAT applied to the Buyer's Fee itself)
- Extra lot fee (if applicable) still incurs 20% VAT
- **No** fixed admin fee

#### 🎯 Two Calculation Modes

**Forward Mode**
- You enter the **bid amount** and the calculator shows a full cost breakdown
- Displays each component separately: hammer price, Buyer's Fee, VAT, extra fee, fixed fee, and total
- Updates in real time as you type

**Reverse Mode**
- You enter your **maximum total budget** and the calculator finds the highest bid that won't exceed it
- Displays the **"Recommended Bid"** — the exact maximum you can bid at the auction
- Ideal when you have a set budget and need to know your ceiling
- Calculated via iterative search with £0.01 precision

#### 📋 Reference Fee Tables
- Full fee tier table for the **Standard Auction** (with Buyer's Fee, VAT, and total)
- Full fee tier table for the **Police Auction**
- Tables switch automatically based on the selected auction type

---

### 🧮 Calculation Logic

**Standard Auction — Forward Mode:**
```
Total = Hammer Price + Buyer's Fee + (Buyer's Fee × 20%) + Extra Fee + (Extra Fee × 20%) + £42.00
```

**Police Auction — Forward Mode:**
```
Total = Hammer Price + Buyer's Fee (ex-VAT) + Extra Fee + (Extra Fee × 20%)
```

**Reverse Mode:**
The calculator iterates from £0.01 up to the remaining budget after deducting fixed fees, testing each possible bid until it finds the highest value whose total cost does not exceed the entered budget.

**Buyer's Fee above table limits:**
- Standard Auction: bids ≥ £12,000 → Buyer's Fee = 6% of hammer price
- Police Auction: bids ≥ £15,000 → Buyer's Fee = 6% of hammer price

---

### 🚀 How to Use

No installation needed. The app is a **single HTML file** with no external dependencies.

1. Download or clone the repository
2. Open `index.html` in any browser — works offline, no internet required
3. Select the auction type (**Standard** or **Police Auction**)
4. Choose the calculation mode:
   - **Forward Mode**: enter your bid → see the total cost
   - **Reverse Mode**: enter your maximum budget → see the maximum bid you can place
5. If the lot has an extra fee, enter it in the corresponding field

> 💡 **Live auction tip:** Pre-fill the Reverse Mode with your total budget before the auction starts. That way, when an interesting lot comes up, you instantly know your bidding ceiling.

---

### 🛠️ Technologies

Intentionally simple — zero dependencies, zero installation.

| Technology | Usage |
|---|---|
| HTML5 | Page structure |
| CSS3 | Styling (no frameworks) |
| Vanilla JavaScript | All calculation logic |

---

### ⚠️ Disclaimer

The fee tables were based on ASM's fee structure at the time this tool was created. Fees may be updated by ASM without prior notice. Always verify final amounts against ASM's official fee schedule before placing a winning bid.
