# 🧰 **Checklist Técnico – Preparação do Ambiente**

> Antes do primeiro encontro, os participantes devem verificar se possuem todas as ferramentas instaladas ou acessíveis (online/local).
> Recomenda-se realizar os testes básicos indicados abaixo para garantir que tudo está funcionando corretamente.

---

### 🔹 **1. Staden Package (Pregap4 / Gap4)**

| Item                    | Detalhes                                                                                                   |
| ----------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Função**              | Edição e montagem de sequências brutas (`.abi`, `.scf`)                                                    |
| **Download**            | [https://staden.sourceforge.net/](https://staden.sourceforge.net/)                                         |
| **Sistema recomendado** | Windows, Linux                                                                        |
| **Teste rápido**        | Abra o **Pregap4**, carregue uma sequência `.abi` e verifique se o eletroferograma é exibido corretamente. |
| **Arquivos de exemplo** | `materials/examples/sequences/raw/*.abi`                                                                        |

---

### 🔹 **2. NCBI BLAST (Web)**

| Item             | Detalhes                                                                                              |
| ---------------- | ----------------------------------------------------------------------------------------------------- |
| **Função**       | Busca de homólogos e confirmação de identidade das sequências                                         |
| **Link**         | [https://blast.ncbi.nlm.nih.gov/Blast.cgi](https://blast.ncbi.nlm.nih.gov/Blast.cgi)                  |
| **Teste rápido** | Execute um BLASTn com uma sequência exemplo do `dataset_final.fasta` e verifique se obtém resultados. |
| **Observação**   | Não requer instalação local.                                                                          |

---

### 🔹 **3. Google Colab + Biopython**

| Item                    | Detalhes                                                                                                 |
| ----------------------- | -------------------------------------------------------------------------------------------------------- |
| **Função**              | Download automatizado de sequências do *GenBank* e manipulação de `FASTA`                                    |
| **Acesso**              | [https://colab.research.google.com/](https://colab.research.google.com/)                                 |
| **Bibliotecas usadas**  | `biopython`, `pandas`                                                                                    |
| **Teste rápido**        | Rode o comando no Colab:<br>`!pip install biopython`<br>`from Bio import Entrez; print("Biopython OK!")` |
| **Notebook de exemplo** | `materials/notebooks/genbank_downloader.ipynb`                                                           |

---

### 🔹 **4. MAFFT**

| Item                   | Detalhes                                                                               |
| ---------------------- | -------------------------------------------------------------------------------------- |
| **Função**             | Alinhamento múltiplo de sequências                                                     |
| **Versão recomendada** | ≥ v7.520                                                                               |
| **Download**           | [https://mafft.cbrc.jp/alignment/software/](https://mafft.cbrc.jp/alignment/software/) |
| **Teste rápido**       | No terminal:<br>`mafft --version`                                                      |
| **Alternativa online** | [MAFFT Web Server](https://mafft.cbrc.jp/alignment/server/)                            |

---

### 🔹 **5. MEGA (Molecular Evolutionary Genetics Analysis)**

| Item                | Detalhes                                                                           |
| ------------------- | ---------------------------------------------------------------------------------- |
| **Função**          | Edição e visualização de alinhamentos                                              |
| **Download**        | [https://www.megasoftware.net/](https://www.megasoftware.net/)                     |
| **Teste rápido**    | Abra o MEGA → *Align → Edit/Build Alignment* → carregue `alignment_cleaned.fasta`. |
| **Versão sugerida** | MEGA 12                                                                  |

---

### 🔹 **6. TrimAl / Gblocks**

| Item                  | Detalhes                                                                                                       |
| --------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Função**            | Limpeza automática do alinhamento                                                                              |
| **Download TrimAl**   | [https://vicfero.github.io/trimal/](https://vicfero.github.io/trimal/)                                                   |
| **Download Gblocks**  | [https://molevol-ibe.csic.es/Gblocks.html](https://molevol-ibe.csic.es/Gblocks.html) |
| **Teste rápido**      | No terminal:<br>`trimal --version` ou `Gblocks alignment.fasta`                                                |
| **Alternativa online** | [https://ngphylogeny.fr/tools/tool/276/form](https://ngphylogeny.fr/tools/tool/276/form) |

---

### 🔹 **7. ModelTest**

| Item             | Detalhes                                                                       |
| ---------------- | ------------------------------------------------------------------------------ |
| **Função**       | Seleção do modelo evolutivo mais adequado                                      |
| **Download**     | [https://evomics.org/resources/software/molecular-evolution-software/modeltest/](https://evomics.org/resources/software/molecular-evolution-software/modeltest/)<br>[https://github.com/ddarriba/modeltest](https://github.com/ddarriba/modeltest) |
| **Teste rápido** | `modeltest-ng -h` deve exibir o help.                                          |
| **Alternativa**  | IQ-TREE (possui ModelFinder embutido).                                         |

---

### 🔹 **8. IQ-TREE 2**

| Item                  | Detalhes                                            |
| --------------------- | --------------------------------------------------- |
| **Função**            | Inferência filogenética por Máxima Verossimilhança  |
| **Download**          | [http://www.iqtree.org/](http://www.iqtree.org/)    |
| **Versão sugerida**   | ≥ 2.3.0                                             |
| **Teste rápido**      | `iqtree2 -h` deve listar os parâmetros disponíveis. |
| **Alternativa online** | [http://iqtree.cibiv.univie.ac.at/](http://iqtree.cibiv.univie.ac.at/) |

---

### 🔹 **9. FigTree / iTOL**

| Item                 | Detalhes                                                                 |
| -------------------- | ------------------------------------------------------------------------ |
| **Função**           | Visualização e anotação de árvores filogenéticas                         |
| **FigTree Download** | [https://tree.bio.ed.ac.uk/software/figtree/](https://tree.bio.ed.ac.uk/software/figtree/) |
| **iTOL Web**         | [https://itol.embl.de/](https://itol.embl.de/)                           |
| **Teste rápido**     | Abra o `.treefile` de exemplo (`materials/example_tree.treefile`).       |
| **Versão sugerida**  | FigTree v1.4.4 ou superior                                               |

---

### ✅ **Checklist Resumido**

| Item                        | Status | Observação                       |
| --------------------------- | :----: | -------------------------------- |
| Staden instalado/testado    |    ☐   | Verificar abertura de `.abi`     |
| Acesso ao NCBI BLAST        |    ☐   | Testar busca com sequência curta |
| Google Colab + Biopython OK |    ☐   | Rodar script de exemplo          |
| MAFFT funcionando           |    ☐   | Executar `mafft --version`       |
| MEGA instalado              |    ☐   | Abrir `alignment_cleaned.fasta`  |
| TrimAl/Gblocks              |    ☐   | Testar comando simples           |
| ModelTest-NG                |    ☐   | Rodar `-h`                       |
| IQ-TREE 2                   |    ☐   | Rodar `iqtree2 -h`               |
| FigTree / iTOL              |    ☐   | Visualizar árvore exemplo        |

