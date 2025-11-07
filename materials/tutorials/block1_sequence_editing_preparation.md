# 🧬 **Bloco 1 – Edição e Preparação de Sequências**

## **0. Objetivo do tutorial**

Este tutorial explica, passo a passo, como:

1. Entender o que são os arquivos de sequência que você vai usar (**`.abi`**, **`.fasta`** e afins).
2. Instalar e configurar o **Staden Package** para editar cromatogramas.
3. Editar uma sequência bruta, fazer o trimming e exportar em formato **`FASTA`**.
4. Conferir a identidade da sequência usando o **NCBI BLAST**.
5. Montar um **dataset inicial de sequências** em formato FASTA, usando **Google Colab + Biopython** para baixar sequências do GenBank.

Ao final do Bloco 1, você deverá ter um arquivo:

```text
dataset_edited_seqs.fasta
```

com as sequências que serão usadas no alinhamento e etapas seguintes do curso.

---

## **1. Conceitos básicos necessários**

Antes de começar, é importante ter clareza sobre alguns conceitos, mesmo que em nível bem introdutório.

### 1.1 DNA e regiões alvo

* **DNA** é a molécula que armazena a informação genética dos organismos.
* Em fungos, algumas regiões comumente usadas em filogenia são:

  * **ITS** (região interna transcrita do rDNA)
  * **LSU** (Large Subunit, região da subunidade maior do rDNA)

<!-- TODO: adicionar um equema -->

* Essas regiões são amplificadas por **PCR**, sequenciadas em um sequenciador (por exemplo, `ABI`), e o resultado são **arquivos de cromatograma**.

### 1.2 Cromatogramas (`.abi`, `.scf`)

* São arquivos brutos gerados pelo sequenciador.
* Cada base (A, T, C, G) aparece como um pico colorido em um gráfico.
* Há erros, ruídos, regiões ruins no início e no fim, que precisam ser **editados**.

<!-- TODO: adicionar um exemplo -->

### 1.3 Formato FASTA (`.fasta`)

* Formato de texto simples, muito usado em bioinformática.
* Estrutura:

    ```text
    >identificador_da_sequencia
    ATGCATGCATGC...
    ```

* A primeira linha começa com `>` e traz um **identificador**.
* As linhas seguintes são a **sequência de nucleotídeos** (A, T, C, G, N).

---

## **2. Visão geral do fluxo do Bloco 1**

1. Pegar um cromatograma de exemplo (`.abi`) de um fungo.
2. Editar e limpar a sequência usando o **Staden**, exportando para FASTA.
3. Rodar **BLASTn** no NCBI para conferir se a sequência realmente é de fungo e qual grupo.
4. Baixar sequências de referência (fungos) do *GenBank* para montar um dataset.
5. Padronizar o cabeçalho das sequências e salvar tudo em `dataset_edited_seqs.fasta`.

---

## **3. Instalação e preparação das ferramentas**

### 3.1 Staden Package

**Função:** editar cromatogramas (`.abi`, `.scf`), visualizar picos, corrigir bases e exportar FASTA.

#### 3.1.1 Download

1. Acesse o site oficial do Staden Package.
2. Baixe a versão adequada ao seu sistema (em geral, **Windows** é o mais tranquilo para usuários iniciantes).

Sugestão de organização: crie uma pasta, por exemplo:

```text
C:\phylo_course\staden\
```

ou, no Linux:

```bash
~/phylo_course/staden/
```

e instale o Staden ali.

#### 3.1.2 Verificação rápida

Depois de instalado:

1. Abra o programa **Pregap4**.
2. Verifique se a interface abre sem erros.
3. Feche o **Pregap4**.
4. Abra o **Gap4**.
5. Verifique se o programa inicializa normalmente.

Se ambos abrem, a instalação básica está ok.

---

### 3.2 Acesso ao NCBI BLAST

**Função:** conferir a identidade da sequência contra o banco de dados do NCBI.

* Você só precisa de um navegador e acesso à internet.
* Tenha em mãos a URL do **BLASTn** (você pode manter salva num arquivo de notas ou no README do curso).

Nenhuma instalação local é necessária.

---

### 3.3 Google Colab e Biopython

**Função:** automatizar o download de sequências do GenBank e manipular `FASTA`.

Pré-requisitos:

* Ter uma conta Google ativa.
* Ter acesso ao Google Colab.

Passos gerais:

1. Acesse o [Google Colab](https://colab.research.google.com/).
2. Garanta que você consegue criar um novo notebook.
3. Vamos instalar o **Biopython** diretamente no Colab (veremos o código mais adiante).

---

## **4. Parte A – Edição de sequências no Staden**

### 4.1 Preparando a pasta de trabalho

Crie uma estrutura simples para este bloco, por exemplo:

```text
phylo_course/
└── bloco1/
    ├── raw_sequences/
    │   ├── ITS_fungus_01.ab1
    │   └── ITS_fungus_02.ab1
    └── edited_sequences/
```

Coloque os cromatogramas na pasta `raw_sequences/`.

### 4.2 Criando um projeto no Pregap4

1. Abra o **Pregap4**.
2. Crie um novo projeto (New Project).
3. Indique uma pasta de saída para os arquivos processados, por exemplo:

    ```text
    phylo_course/bloco1/staden_project/
    ```

4. Na etapa de entrada de arquivos, selecione os arquivos `.ab1` ou `.abi` em `raw_sequences/`.

O **Pregap4** irá:

* Ler os cromatogramas.
* Tentar chamar as bases automaticamente.
* Gerar arquivos intermediários que depois poderão ser abertos no Gap4.

### 4.3 Abrindo a sequência no Gap4

1. Depois que o **Pregap4** terminar, abra o **Gap4**.
2. Selecione o banco de dados gerado pelo **Pregap4** (geralmente um arquivo com extensão específica do Staden, por exemplo `.0` ou similar).
3. Procure pela sequência de interesse (por identificação ou pela lista).

### 4.4 Entendendo a janela de cromatograma

Dentro do **Gap4**, ao abrir uma sequência:

* Você verá os **picos coloridos** correspondendo às bases A, T, C, G.
* Abaixo, verá uma **linha de texto** com a sequência chamada automaticamente.
* Regiões no início e no fim costumam ter picos ruins, sobrepostos ou com baixa resolução.

### 4.5 Edição manual básica

Objetivo: corrigir erros evidentes e remover regiões ruins.

Passos típicos:

1. Percorra a sequência da esquerda para a direita.
2. Quando um pico estiver claramente mal chamado (por exemplo, a letra não corresponde ao pico predominante), clique no caractere da base e altere para a base correta.
3. Se houver trechos muito ruins, com muitos picos sobrepostos, considere substituí-los por `N` (base desconhecida).
4. Nos primeiros e últimos nucleotídeos, se a qualidade for muito baixa, você pode cortar essas regiões. O Staden possui ferramentas para marcar regiões a serem removidas; o procedimento exato varia um pouco conforme a versão, mas a lógica é:

   * Selecionar o intervalo.
   * Marcar como “clipped” ou cortado.

A ideia aqui não é atingir perfeição, mas obter uma sequência **razoavelmente confiável** para a análise.

### 4.6 Exportando a sequência em FASTA

Depois de editar:

1. No **Gap4**, procure a opção de **exportar sequência** (por exemplo, na barra de menus, algo como “Export” ou “Save As”).
2. Escolha formato **FASTA**.
3. Defina um nome de arquivo descritivo, por exemplo:

```text
ITS_fungus_01_edited.fasta
```

4. Salve o arquivo na pasta:

```text
phylo_course/bloco1/edited_sequences/
```

Abra o arquivo `.fasta` em um editor de texto simples (Notepad, VSCode, etc.) e verifique se ele está no formato esperado:

```text
>ITS_fungus_01_edited
ATGCCTGA...
```

---

## **5. Parte B – Conferindo a sequência com BLAST (NCBI)**

Agora vamos conferir se a sua sequência editada faz sentido biologicamente.

### 5.1 Acessando o BLASTn

1. Abra o navegador.
2. Acesse a página do **BLASTn** (NCBI).
3. Você verá uma caixa de texto para inserir a sequência.

### 5.2 Preparando a sequência

1. Abra o arquivo `ITS_fungus_01_edited.fasta`.
2. Copie apenas a parte da sequência, ou, se preferir, todo o FASTA (o BLAST aceita o formato FASTA diretamente).

Exemplo:

```text
>ITS_fungus_01_edited
ATGCCTGA...
```

3. Cole na caixa de texto do **BLAST**.

### 5.3 Configurando o BLAST

Use uma configuração básica para começar:

* **Program selection**: Nucleotide BLAST (BLASTn).
* **Database**: por exemplo, `nt` (nucleotide collection).
* **Organism (opcional)**: você pode filtrar para `Fungi` mais tarde, mas inicialmente vale ver o que aparece.

Clique em **BLAST**.

### 5.4 Interpretando os resultados

Quando o BLAST terminar:

* Olhe a lista de **Top hits**.
* Verifique:

  * Identidade (% identity).
  * Cobertura (query cover).
  * E-value.
* Idealmente, você deve ver hits para fungos, preferencialmente do grupo esperado (por exemplo, Basidiomycota, Ascomycota, gênero X etc.).

Se os melhores hits tiverem:

* Identidade alta (por exemplo, > 95 %).
* Cobertura alta.

Então a sua sequência está coerente com o grupo de fungos esperado.

### 5.5 Salvando sequências de referência

Você pode selecionar alguns **acession numbers** (por exemplo, 10, 20 ou mais) dos melhores hits para montar seu dataset.

Sugestão:

* Copiar num bloco de notas uma lista de accessions, por exemplo:

```text
OK123456
MN789101
AJ234567
...
```

Guarde essa lista, pois vamos usá-la no Colab.

---

## **6. Parte C – Montando o dataset no Google Colab com Biopython**

Agora vamos usar **Python + Biopython** no **Google Colab** para baixar as sequências do GenBank e criar um `dataset_edited_seqs.fasta`.

### 6.1 Criando o notebook no Colab

1. Acesse o [Google Colab](https://colab.research.google.com/).
2. Clique em **New Notebook**.
3. Renomeie o notebook para algo como:

```text
bloco1_genbank_dataset.ipynb
```

### 6.2 Instalando o Biopython no Colab

Na primeira célula, execute:

```python
!pip install biopython
```

Aguarde a instalação terminar.
Se tudo der certo, você verá uma mensagem indicando que o Biopython foi instalado.

### 6.3 Configurando o Biopython (Entrez)

Na célula seguinte, vamos importar as bibliotecas e configurar o e-mail (o NCBI pede um e-mail de contato):

```python
from Bio import Entrez, SeqIO

# Substitua pelo seu e-mail real
Entrez.email = "seu_email@exemplo.com"
```

### 6.4 Criando a lista de accessions

Você pode colocar diretamente a lista de accessions que salvou do BLAST:

```python
accessions = [
    "OK123456",
    "MN789101",
    "AJ234567",
    # adicione aqui os outros códigos
]
```

### 6.5 Baixando sequências do GenBank

Vamos fazer uma função simples para baixar as sequências em formato FASTA:

```python
def fetch_sequences_from_genbank(accession_list, output_fasta):
    """
    Faz download de sequências do GenBank em formato FASTA
    e salva em um arquivo único.
    """
    handle = Entrez.efetch(
        db="nucleotide",
        id=",".join(accession_list),
        rettype="fasta",
        retmode="text"
    )
    fasta_data = handle.read()
    handle.close()

    with open(output_fasta, "w") as f:
        f.write(fasta_data)

    print(f"Arquivo FASTA salvo como: {output_fasta}")
```

Agora, chame a função:

```python
output_file = "genbank_references_raw.fasta"
fetch_sequences_from_genbank(accessions, output_file)
```

No ambiente do Colab, esse arquivo será salvo no sistema de arquivos temporário.

### 6.6 Padronizando cabeçalhos (opcional, mas recomendado)

Geralmente, os cabeçalhos do GenBank são longos e cheios de informações. Para facilitar a análise, podemos gerar um novo FASTA com cabeçalhos padronizados.

Por exemplo, algo como:

```text
>FUNGUS_01_OK123456
>FUNGUS_02_MN789101
...
```

Código sugerido:

```python
def clean_fasta_headers(input_fasta, output_fasta, prefix="FUNGUS_"):
    records = list(SeqIO.parse(input_fasta, "fasta"))
    cleaned_records = []

    for i, rec in enumerate(records, start=1):
        # Usa o accession original (primeira palavra do id original)
        original_id = rec.id.split("|")[0]
        new_id = f"{prefix}{i:02d}_{original_id}"
        rec.id = new_id
        rec.name = new_id
        rec.description = ""
        cleaned_records.append(rec)

    SeqIO.write(cleaned_records, output_fasta, "fasta")
    print(f"FASTA com cabeçalhos limpos salvo como: {output_fasta}")
```

Em seguida, rode:

```python
clean_fasta_headers("genbank_references_raw.fasta", "genbank_references_clean.fasta")
```

### 6.7 Unindo sua sequência editada com as referências

Você tem:

* Sua sequência editada (por exemplo, `ITS_fungus_01_edited.fasta`).
* As sequências de referência do GenBank (`genbank_references_clean.fasta`).

Você pode:

1. Fazer upload da sua sequência editada para o Colab (menu lateral, aba de arquivos → upload).
2. Em seguida, concatenar os FASTA.

Exemplo simples em Python:

```python
input_files = [
    "ITS_fungus_01_edited.fasta",      # sua sequência
    "genbank_references_clean.fasta",  # referências
]

output_dataset = "dataset_final.fasta"

with open(output_dataset, "w") as outfile:
    for fname in input_files:
        with open(fname) as infile:
            outfile.write(infile.read())

print(f"Dataset final salvo como: {output_dataset}")
```

### 6.8 Baixando o `dataset_final.fasta` para seu computador

No Colab:

1. Use:

```python
from google.colab import files
files.download("dataset_final.fasta")
```

2. O navegador irá baixar o arquivo.
3. Salve em:

```text
phylo_course/bloco1/dataset_final.fasta
```

Esse será o arquivo usado no **Bloco 2 (Alinhamento e Limpeza)**.

---

## 7. Boas práticas para o Bloco 1

* Sempre mantenha uma cópia dos arquivos **brutos** (`raw_sequences/`) intacta.
* Documente as mudanças relevantes (por exemplo, quantos nucleotídeos foram cortados na extremidade, se houve muitas correções manuais).
* Use identificadores claros para as sequências, especialmente se forem de projetos reais (por exemplo, misture informações mínimas: código da amostra, gene, espécie se conhecida).
* Evite espaços em branco e caracteres especiais nos cabeçalhos FASTA. Use apenas letras, números, `_` e, se necessário, `-`.
