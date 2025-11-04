# 🧬 **Curso Prático de Análise Filogenética – Cronograma Interativo**

> 📅 **Início:** Segunda-feira, **10/11**, às **10h**   
> 👩🏻‍🏫 **Instrutora:** [*Angelina de Meiras-Ottoni*](https://www.linkedin.com/in/angelina-meiras-ottoni/)    
> 🧠 **Foco:** Pipeline completo de análise filogenética, do DNA à árvore final  
> 📍 **Formato:** _a definir_   

---

## ✅ **Status Geral**

| Etapa                                          | Progresso |
| ---------------------------------------------- | --------- |
| 🔹 Bloco 1 – Edição e Preparação de Sequências | ☐         |
| 🔹 Bloco 2 – Alinhamento e Limpeza             | ☐         |
| 🔹 Bloco 3 – Seleção do Modelo Evolutivo       | ☐         |
| 🔹 Bloco 4 – Construção da Árvore (ML)         | ☐         |
| 🔹 Bloco 5 – Visualização e Interpretação      | ☐         |

---

## 🧩 **Encontro 1 – Edição e Preparação de Sequências**

📅 **Data:** Segunda-feira, 10/11 — ⏰ 10h  
🎯 **Objetivo:** Introduzir o pipeline e preparar o dataset inicial.

**Atividades**

* [ ] Introdução à análise filogenética 
* [ ] Instalar **Staden** e abrir sequência `.abi`
* [ ] Editar e exportar para `.fasta`
* [ ] Rodar **BLASTn** no NCBI
* [ ] Usar **Biopython (Colab)** para baixar sequências do GenBank
* [ ] Montar dataset final (`dataset_edited_seqs.fasta`)

**Materiais**

* 📁 [Sequências de exemplo](materials/examples/sequences/raw/)
* 📓 [Notebook Colab – GenBank Downloader](../materials/notebooks/genbank_downloader.ipynb)

**Entrega esperada**

* [ ] `dataset_edited_seqs.fasta`

---

## 🧩 **Encontro 2 – Alinhamento e Limpeza**

📅 **Data:** _a definir_
🎯 **Objetivo:** Produzir um alinhamento limpo e confiável.

**Atividades**

* [ ] Executar **MAFFT** (local ou online)
* [ ] Revisar no **MEGA** (edição manual)
* [ ] Limpar com **Gblocks** ou **TrimAl**
* [ ] Exportar `alignment_cleaned.fasta`

**Materiais**

* 📁 [Dataset final do grupo](results/dataset_final.fasta)
* 💻 [MAFFT Web Server](https://mafft.cbrc.jp/alignment/server/)

**Entrega esperada**

* [ ] `alignment_cleaned.fasta`

---

## 🧩 **Encontro 3 – Seleção de Modelo Evolutivo**

📅 **Data:** _a definir_    
🎯 **Objetivo:** Identificar o modelo evolutivo mais adequado.

**Atividades**

* [ ] Executar **ModelTest-NG** ou **IQ-TREE (-m TEST)**
* [ ] Comparar modelos (AIC, BIC, AICc)
* [ ] Registrar o modelo escolhido

**Materiais**

* 💻 [ModelTest-NG Download](https://github.com/ddarriba/modeltest)
* 📓 [Exemplo de saída do IQ-TREE](../materials/examples/example_model_selection.txt)

**Entrega esperada**

* [ ] `model_selection.txt`

---

## 🧩 **Encontro 4 – Construção da Árvore (Máxima Verossimilhança)**

📅 **Data:** _a definir_    
🎯 **Objetivo:** Gerar a árvore filogenética a partir do alinhamento limpo e interpretar os resultados.

**Atividades**

* [ ] Rodar IQ-TREE com modelo escolhido

  ```bash
  iqtree2 -s alignment_cleaned.fasta -m GTR+G+I -B 1000 -T AUTO
  ```
* [ ] Verificar arquivos `.log`, `.iqtree`, `.treefile`
* [ ] Interpretar valores de bootstrap (SH-aLRT e [UFBoot](https://iqtree.github.io/doc/Frequently-Asked-Questions#how-do-i-interpret-ultrafast-bootstrap-ufboot-support-values))

**Materiais**

* 📘 [Guia rápido – Comandos IQ-TREE](tutorials/iqtree_commands.pdf)
* 📁 [Exemplo de árvore inferida](materials/example_tree.treefile)

**Entrega esperada**

* [ ] `treefile` (árvore inferida)

---

## 🧩 **Encontro 5 – Visualização e Interpretação**

📅 **Data:** _a definir_
🎯 **Objetivo:** Visualizar e discutir a topologia da árvore final.

**Atividades**

* [ ] Abrir árvore no **FigTree**
* [ ] Ajustar raiz, rótulos e escala
* [ ] Discutir clados e valores de suporte
* [ ] Exportar árvore final em PDF ou formato desejado

**Materiais**

* 💻 [FigTree](https://github.com/rambaut/figtree)
* 🌐 [iTOL (Interactive Tree Of Life)](https://itol.embl.de/)

**Entrega esperada**

* [ ] `final_tree.pdf`

---

## 🌱 **Encerramento**

* [ ] Revisão geral do pipeline
* [ ] Discussão sobre alternativas (Bayesian inference, BEAST, RAxML)
* [ ] Entrega dos arquivos finais e feedback do grupo
* [ ] Coleta de sugestões para melhorias ou módulos avançados

---

### ✉️ **Organização e Contato**

📧 Enviar e-mail para participação: `angel.m.ottoni@gmail.com`
📤 Materiais e links de cada encontro serão enviados antecipadamente.
💬 Grupo de apoio: *(a ser definido — Telegram ou WhatsApp)*

