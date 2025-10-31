# 🧾 Razão PDF → Excel (Tabular)

<p align="center">
  <img src="https://img.shields.io/badge/Made%20with-Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/github/license/suelenfariass/razao-pdf2excel?style=for-the-badge"/>
  <img src="https://img.shields.io/github/stars/suelenfariass/razao-pdf2excel?style=for-the-badge&color=yellow"/>
  <img src="https://img.shields.io/github/last-commit/suelenfariass/razao-pdf2excel?style=for-the-badge&color=orange"/>
</p>

> **Transforme PDFs de Razão Contábil em planilhas Excel tabuladas, prontas para análise.**  
> Um utilitário simples, rápido e open source feito com **pandas**, **pdfplumber** e **openpyxl**.

---

## 🚀 O que é

O **Razão PDF → Excel** é um script em Python que lê relatórios de Razão Contábil em PDF e exporta os lançamentos de forma **estruturada em Excel**, mantendo colunas padronizadas como:

| Dt. Movto | Lote | Lanç | Histórico | Débito | Crédito | Saldo Acum |
|------------|-------|-------|------------|----------|-----------|-------------|
| 01/01/2025 | 12 | 1 | Pagamento de fornecedor | 10.000,00 | 0,00 | 10.000,00C |

Ideal para:
- Contadores e controllers que recebem o Razão em PDF;
- Analistas de dados que precisam importar lançamentos para o Power BI, Excel ou Python;
- Quem quer automatizar a conversão de relatórios contábeis para bases estruturadas.

---

## 🛠️ Stack principal

- 🐍 [Python 3.9+](https://www.python.org/)
- 🧩 [pandas](https://pandas.pydata.org/)
- 📄 [pdfplumber](https://github.com/jsvine/pdfplumber)
- 📘 [openpyxl](https://openpyxl.readthedocs.io/)

---

## ⚙️ Instalação

Clone o repositório e instale as dependências:

```bash
git clone https://github.com/suelenfariass/razao-pdf2excel.git
cd razao-pdf2excel

python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

pip install -r requirements.txt
```

---

## ▶️ Uso

```bash
python src/razao_pdf2xlsx.py --pdf "entrada.pdf" --out "saida.xlsx"
```

### Argumentos disponíveis

| Flag | Descrição |
|------|------------|
| `--pdf` | Caminho do PDF de entrada |
| `--out` | Caminho do arquivo Excel de saída |
| `--sheet-name` | Nome da aba no Excel (padrão: `lancamentos`) |
| `--ignore` | Linha/padrão adicional para ignorar (pode repetir a flag) |

### Exemplo prático

```bash
python src/razao_pdf2xlsx.py ^
  --pdf ".\examples\RAZAO_EXEMPLO.pdf" ^
  --out ".\out\razao_exemplo.xlsx" ^
  --ignore "Relatório Contábil" ^
  --ignore "Empresa XYZ S.A."
```

💡 **Dica:** use `--ignore` para eliminar cabeçalhos e rodapés personalizados do seu relatório.

---

## 🧠 Como funciona

1. Detecta automaticamente cada lançamento pelo padrão `DD/MM/AAAA  LOTE  LANC` em qualquer ponto da linha;  
2. Agrupa todas as linhas de um mesmo lançamento (incluindo continuações);  
3. Extrai os três valores principais (`Débito`, `Crédito`, `Saldo Acum`) e limpa o histórico;  
4. Gera um Excel tabulado e pronto para análise.

---

## ⚡ Exemplo visual

```text
01/01/2025   12   1   Pagamento fornecedor X  10.000,00  0,00  10.000,00C
02/01/2025   12   2   Recebimento cliente Y    0,00     3.500,00  6.500,00D
```

⬇️  
Gera automaticamente:

| Dt. Movto | Lote | Lanç | Histórico | Débito | Crédito | Saldo Acum |
|------------|-------|-------|------------|----------|-----------|-------------|
| 01/01/2025 | 12 | 1 | Pagamento fornecedor X | 10.000,00 | 0,00 | 10.000,00C |
| 02/01/2025 | 12 | 2 | Recebimento cliente Y | 0,00 | 3.500,00 | 6.500,00D |

---

## 📂 Estrutura do projeto

```
razao-pdf2excel/
├─ src/
│  └─ razao_pdf2xlsx.py
├─ examples/
│  └─ README.md
├─ tests/
│  └─ test_placeholder.md
├─ .gitignore
├─ LICENSE
├─ README.md
├─ requirements.txt
├─ CHANGELOG.md
└─ CONTRIBUTING.md
```

---

## 🧩 Roadmap

- [x] Parser robusto com regex dinâmica  
- [x] CLI com argparse  
- [ ] Adicionar suporte a múltiplos PDFs por pasta  
- [ ] Exportação opcional para `.parquet`  
- [ ] Publicação no PyPI (`pip install razao-pdf2excel`)  

---

## 💬 Contribuindo

Quer ajudar a melhorar o projeto?

1. Faça um **fork**  
2. Crie uma branch (`git checkout -b feature/nova-feature`)  
3. Commit suas alterações (`git commit -m "feat: nova feature"`)  
4. Push para sua branch (`git push origin feature/nova-feature`)  
5. Abra um **Pull Request** 💙

Mais detalhes em [`CONTRIBUTING.md`](CONTRIBUTING.md)

---

## 🪪 Licença

Distribuído sob a licença **MIT** — veja [`LICENSE`](LICENSE) para mais detalhes.

---

## 🌟 Apoie o projeto

Se esse utilitário te ajudou, deixe uma ⭐ no repositório!  
Isso incentiva o desenvolvimento de mais ferramentas para automação contábil e financeira.

<p align="center">
  <img src="https://img.shields.io/badge/Feito_com_💙_por-Suelen%20Farias-8A2BE2?style=for-the-badge"/>
</p>
