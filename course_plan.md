# 🧬 **Plano de Ensino – Introdução Prática à Análise Filogenética**

**Público-alvo:** estudantes e pesquisadores de biologia que já conhecem conceitos básicos de DNA, mas nunca realizaram uma análise filogenética completa.  
**Formato:** encontros práticos guiados (2h cada).    
**Objetivo:** capacitar o participante a construir e interpretar uma árvore filogenética, usando ferramentas acessíveis e gratuitas.

---

### 🔹 **Bloco 1 — Edição e Preparação de Sequências (Staden, BLAST, Biopython)**

**Objetivo:** preparar dados de sequência confiáveis para análise.

#### 🧠 Conceitos:

* O que são sequências ITS/LSU, COI, etc.
* Qualidade, trimming, orientação e formatação FASTA.
* Diferença entre sequências “brutas”, “editadas” e “curadas”.

#### ⚙️ Ferramentas e materiais:

| Etapa              | Ferramenta                     | Material a preparar/disponibilizar                                            |
| ------------------ | ------------------------------ | ----------------------------------------------------------------------------- |
| Edição             | **Staden (Pregap4, Gap4)**     | Arquivo `.abi` ou `.scf` de exemplo (sequências reais curtas)                 |
| Busca de homólogos | **NCBI BLAST (web)**           | Links para BLASTn + instruções para salvar resultados                         |
| Dataset            | **Python + Biopython (Colab)** | Notebook com script para baixar e renomear sequências do GenBank via `Entrez` |

#### 🧩 Dinâmica:

1. Mostrar um exemplo de sequência bruta e editar ao vivo no Staden.
2. Explicar como exportar para `.fasta`.
3. Demonstrar busca BLAST e como escolher sequências de referência.
4. No Colab, montar o dataset final (`.fasta`) com cabeçalhos padronizados.

#### 📦 Entrega esperada:

* Arquivo `dataset_edited_seqs.fasta` contendo as sequências do grupo.

---

### 🔹 **Bloco 2 — Alinhamento e Limpeza (MAFFT, MEGA, TrimAl/Gblocks)**

**Objetivo:** gerar alinhamentos reprodutíveis e prontos para análise.

#### ⚙️ Ferramentas:

* **MAFFT (<ins>online</ins> ou ~~local~~)**
* **MEGA n** para inspeção manual
* **Gblocks** ou **TrimAl** para limpeza automática

#### 📁 Materiais:

* `dataset_edited_seqs.fasta` (gerado no bloco anterior)
* Slides/resumo com boas práticas: gaps, blocos conservados, regiões ambíguas

#### 🧩 Dinâmica:

1. Executar alinhamento no MAFFT Online Version.
2. Salvar em formato `.fasta`.
3. Editar manualmente no MEGA (mostrar regiões ruins).
4. Demonstrar uso do Gblocks/TrimAl para limpeza automática.

#### 📦 Entrega esperada:

* `alignment_cleaned.fasta`

---

### 🔹 **Bloco 3 — Seleção de Modelo Evolutivo (ModelTest-NG e IQ-TREE)**

**Objetivo:** compreender e aplicar o modelo evolutivo ideal antes da inferência.

#### ⚙️ Ferramentas:

* **ModelTest-NG**
* **IQ-TREE (com ModelFinder embutido)**

#### 📁 Materiais:

* Arquivo `alignment_cleaned.fasta`
* Tabela resumindo modelos comuns (JC, K2P, GTR, etc.)

#### 🧩 Dinâmica:

1. Executar o ModelTest-NG (ou IQ-TREE com `-m TEST`).
2. Discutir critérios (AIC, BIC, AICc).
3. Registrar o modelo selecionado (ex: GTR+G+I).

#### 📦 Entrega esperada:

* Relatório do modelo (ex: `model_selection.txt`)

---

### 🔹 **Bloco 4 — Construção da Árvore (IQ-TREE)**

**Objetivo:** realizar a inferência por Máxima Verossimilhança.

#### ⚙️ Ferramentas:

* **IQ-TREE (linha de comando)**

#### 📁 Materiais:

* `alignment_cleaned.fasta`
* Modelo escolhido (`model_selection.txt`)

#### 🧩 Dinâmica:

1. Executar comando completo (ex: `iqtree2 -s alignment_cleaned.fasta -m GTR+G+I -B 1000 -T AUTO`).
2. Explicar os arquivos gerados (`.treefile`, `.log`, `.iqtree`).
3. Discutir interpretação básica dos valores de bootstrap.

#### 📦 Entrega esperada:

* `treefile` final para visualização.

---

### 🔹 **Bloco 5 — Visualização e Interpretação (FigTree, Discussão)**

**Objetivo:** visualizar, editar e interpretar a topologia da árvore.

#### ⚙️ Ferramentas:

* **FigTree** (local)
* **iTOL** (opcional, online)

#### 📁 Materiais:

* Arquivo `.treefile`
* Slide com exemplos de clados e monofilia/parafilia

#### 🧩 Dinâmica:

1. Abrir a árvore no FigTree.
2. Ajustar rótulos, bootstrap, raízes.
3. Discutir clados principais, suporte e implicações.

#### 📦 Entrega esperada:

* `final_tree.pdf`.

---

### 🔹 **Encerramento e Continuidade**

* Relembrar boas práticas (documentar pipeline, salvar versões FASTA/Tree).
* Discutir possibilidades de extensão (Bayesian Inference, multi-gene, BEAST, RAxML).
* Coletar feedback e planejar o próximo módulo.

---
