# 🤝 Guia de Contribuição

Este documento descreve as diretrizes para contribuir com o repositório **phylo-course-amo**  
(Curso Prático de Análise Filogenética – autoria de *Angelina de Meiras-Ottoni*).

---

## 🧱 Estrutura do Repositório

```

phylo-course-amo/
├── materials/              → dados, tutoriais e notebooks
├── results/                → resultados dos participantes
├── docs/                   → documentação técnica e cronogramas
├── course_plan.md          → plano geral do curso
├── LICENSE                 → licença MIT
└── README.md               → visão geral do projeto

```

---

## 🌿 Fluxo de Contribuição

1. **Abra uma Issue** descrevendo o que deseja propor:  
   - correção de erros ou ajustes de formatação;  
   - inclusão de novos exemplos, dados ou tutoriais;  
   - melhorias de clareza ou atualização de ferramentas.

2. **Crie uma Branch** específica para sua contribuição:  
   Use o padrão semântico:

```

docs/update-tutorial-mafft
feat/add-notebook-modeltest
fix/typo-in-checklist

```

> O prefixo indica o tipo de alteração (`docs`, `feat`, `fix`, etc.).

3. **Faça Commits Claros e Padronizados**

Siga o formato [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/):

```

tipo(escopo opcional): descrição breve

```

Exemplos:
```

docs: add installation guide for IQ-TREE
feat: include new GenBank downloader notebook
fix: correct typo in ModelTest tutorial

```

4. **Envie um Merge Request (MR)**  
- Garanta que o MR descreve claramente o propósito da mudança.  
- Associe a Issue correspondente usando `Closes #N`.  
- Mantenha um histórico limpo e conciso (use `rebase` se necessário).  

---

## 🧰 Boas Práticas

- Mantenha **consistência terminológica** (ex.: nomes de ferramentas, parâmetros, blocos).  
- Evite arquivos pesados (>10 MB) — prefira links externos (Zenodo, GDrive, etc.).  
- Use sempre **nomes em inglês** para arquivos e pastas internas.  
- Inclua comentários explicativos em scripts e notebooks.  
- Quando adicionar dados de exemplo, inclua a **fonte e o contexto biológico** (ex.: espécie, gene, GenBank ID).  

---

## 🧩 Tipos de Contribuições Bem-Vindas

- Correções em documentação e formatação  
- Adição de tutoriais ou exemplos de pipelines  
- Melhoria de instruções de instalação ou execução  
- Tradução e internacionalização do material  
- Adição de ferramentas livres equivalentes para outros sistemas operacionais  

---

## 🧾 Licenciamento

Ao contribuir, você concorda que suas modificações serão disponibilizadas sob as mesmas licenças do repositório:

- **MIT License** → para códigos, scripts e notebooks  
- **CC BY 4.0** → para materiais didáticos e documentação  

---

🧬 *Este projeto faz parte das iniciativas educacionais da autora.*      
*Manter o padrão e a clareza contribui para a reprodutibilidade e o impacto coletivo das atividades de ensino e pesquisa.*

