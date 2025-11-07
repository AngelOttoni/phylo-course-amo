# 🧬 Curso Prático de Análise Filogenética

> 📅 **Início:** Segunda-feira, **10/11**, às **10h**  
> 👩🏻‍🏫 **Instrutora:** [*Angelina de Meiras-Ottoni*](https://www.linkedin.com/in/angelina-meiras-ottoni/)     
> 🧠 **Foco:** Pipeline completo de análise filogenética — do DNA à árvore final          
> 💻 **Plataforma:** GitHub (materiais, notebooks e resultados compartilhados)  
> 📍 **Formato:** Curso prático/Online 

---

## 📘 **Descrição**

Este curso tem como objetivo apresentar, de forma prática e guiada, todas as etapas envolvidas em uma **análise filogenética completa** — desde a edição e curadoria de sequências até a inferência e visualização da árvore.

O foco é o **uso aplicado de ferramentas acessíveis**, tanto locais quanto online, aliado à compreensão dos conceitos fundamentais necessários para garantir resultados reprodutíveis e de qualidade.

---

## 🧭 **Pipeline de Aprendizado**

```

Sequência bruta (.abi/.scf)
↓
Edição e curadoria (Staden + BLAST + Biopython)
↓
Alinhamento e limpeza (MAFFT, MEGA, TrimAl/Gblocks)
↓
Seleção do modelo evolutivo (ModelTest-NG / IQ-TREE)
↓
Inferência filogenética (IQ-TREE – ML)
↓
Visualização e interpretação (FigTree)

```

---

## 📂 **Como Usar este Repositório**

O repositório está organizado para facilitar o acompanhamento dos blocos do curso e a reprodutibilidade das análises:

```
phylo-course-amo/
├── LICENSE                   → licenças MIT (código) e CC BY 4.0 (materiais)
├── README.md                 → visão geral do curso e instruções principais
├── course_plan.md            → plano geral do curso (objetivos, metodologia e módulos)
├── docs/                     → documentação complementar
│   ├── technical_checklist.md → guia técnico de instalação e configuração
│   └── course_schedule.md     → cronograma interativo do curso
├── materials/                → dados, tutoriais e notebooks utilizados em aula
│   ├── examples/             → exemplos de análise e seleção de modelo
│   │   ├── example_model_selection.txt
│   │   └── sequences/
│   │       └── raw/          → sequências brutas de exemplo (.fasta, .abi etc.)
│   ├── notebooks/            → notebooks práticos (ex.: *genbank_downloader.ipynb*)
│   └── tutorials/            → tutoriais passo a passo (ex.: *block1_sequence_editing_preparation.md*)
└── results/                  → resultados gerados durante o curso
```

**Como navegar:**

1. Comece consultando o arquivo [`docs/technical_checklist.md`](./docs/technical_checklist.md) para preparar seu ambiente.
2. Acompanhe o cronograma em [`docs/course_schedule.md`](./docs/course_schedule.md) para saber o conteúdo de cada encontro.
3. Explore o diretório [`materials/`](./materials) conforme as instruções durante as aulas.
4. Armazene seus resultados ou relatórios pessoais em [`results/participants/`](./results/participants/).

---

## 📑 **Documentação Adicional**

- 🔧 [**Checklist Técnico**](docs/technical_checklist.md): guia básico de instalação e configuração para todas as ferramentas.
- 🗓️ [**Cronograma do Curso**](docs/course_schedule.md): cronograma interativo com materiais e resultados esperados.

---

## 🤖 **Transparência e Ferramentas de Apoio**

Parte da organização e documentação deste curso contou com o **apoio do modelo de linguagem ChatGPT 5 (OpenAI)**, utilizado como ferramenta de **revisão textual, estruturação de conteúdos e padronização de templates**.
Todas as decisões conceituais, revisões e materiais didáticos foram supervisionados e validados por *Angelina de Meiras-Ottoni*.

---

## ⚖️ **Licença**

Este repositório é distribuído sob **duas licenças complementares**:

- **Código-fonte e scripts** (por exemplo, notebooks e utilitários em Python): licenciados sob a [**MIT License**](./LICENSE), permitindo uso, modificação e redistribuição com atribuição de autoria.  
- **Materiais didáticos e documentações** (por exemplo, tutoriais, cronogramas e planos de curso): licenciados sob a [**Creative Commons Attribution 4.0 International (CC BY 4.0)**](https://creativecommons.org/licenses/by/4.0/), permitindo uso e adaptação com a devida atribuição à autora.

📚 *Você é livre para reutilizar, remixar e compartilhar os conteúdos deste curso, desde que mantenha a referência a Angelina de Meiras-Ottoni como autora original.*

---

## 🤝 **Contribuindo**

Contribuições são bem-vindas para aprimorar o material e os exemplos do curso!  

Consulte o guia completo de contribuição: [`CONTRIBUTING.md`](./CONTRIBUTING.md).  
*Ele contém todas as instruções sobre criação de Issues, branches, commits e Pull Requests, além das boas práticas de colaboração.*

> As contribuições devem manter o estilo didático, reprodutível e compatível com o escopo do curso.

💡 Sugestões de novos blocos, tutoriais ou exemplos de dados reais são especialmente bem-vindas.

---


## ✉️ **Contato e Organização**

📧 Interessados devem enviar e-mail para: **[angel.m.ottoni@gmail.com](mailto:angel.m.ottoni@gmail.com)**   
📤 Materiais e links de cada encontro serão enviados com antecedência.  
💬 Grupo de apoio: *(a definir – Telegram ou WhatsApp)* 

---

🧩 *Documento elaborado por Angelina de Meiras-Ottoni para fins educacionais e treinamento aplicado em análise filogenética.*

