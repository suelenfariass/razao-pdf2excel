# Razão PDF → Excel (Tabular)

[![Made with Python](https://img.shields.io/badge/Made%20with-Python-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/github/license/suelenfariass/razao-pdf2excel?style=flat)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/suelenfariass/razao-pdf2excel?style=flat&color=yellow)](https://github.com/suelenfariass/razao-pdf2excel/stargazers)
[![Last Commit](https://img.shields.io/github/last-commit/suelenfariass/razao-pdf2excel?style=flat&color=orange)](https://github.com/suelenfariass/razao-pdf2excel)

---

## Descrição

**Razão PDF → Excel** é um utilitário em Python desenvolvido para extrair lançamentos contábeis de relatórios de Razão em PDF e convertê-los para um formato tabular em Excel.  

O projeto tem como objetivo facilitar a análise de dados contábeis, automatizando a estruturação de relatórios frequentemente distribuídos apenas em PDF.

---

## Principais Recursos

- Leitura e extração automática de lançamentos contábeis.
- Identificação de campos `Data`, `Lote`, `Lançamento`, `Histórico`, `Débito`, `Crédito` e `Saldo Acumulado`.
- Remoção de cabeçalhos e rodapés de páginas.
- Exportação direta para Excel (`.xlsx`).
- Interface de linha de comando (CLI) simples e personalizável.

---

## Tecnologias Utilizadas

- [Python 3.9+](https://www.python.org/)
- [pandas](https://pandas.pydata.org/)
- [pdfplumber](https://github.com/jsvine/pdfplumber)
- [openpyxl](https://openpyxl.readthedocs.io/)

---

## Instalação

Clone o repositório e instale as dependências necessárias:

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

## Uso

Execute o script principal informando o arquivo PDF de entrada e o caminho de saída do Excel:

```bash
python src/razao_pdf2xlsx.py --pdf "entrada.pdf" --out "saida.xlsx"
```

### Argumentos disponíveis

| Argumento | Descrição |
|------------|------------|
| `--pdf` | Caminho do arquivo PDF de entrada |
| `--out` | Caminho do arquivo Excel de saída |
| `--sheet-name` | Nome da planilha no Excel (padrão: `lancamentos`) |
| `--ignore` | Texto adicional a ser ignorado durante a leitura (pode ser repetido) |

### Exemplo

```bash
python src/razao_pdf2xlsx.py ^
  --pdf ".\examples\RAZAO_EXEMPLO.pdf" ^
  --out ".\out\razao_exemplo.xlsx" ^
  --ignore "Relatório Contábil" ^
  --ignore "Empresa XYZ S.A."
```

---

## Funcionamento

1. O script identifica linhas de lançamento pelo padrão `DD/MM/AAAA  LOTE  LANC`.
2. Agrupa linhas contínuas que pertencem ao mesmo lançamento.
3. Extrai os valores de `Débito`, `Crédito` e `Saldo`.
4. Gera uma planilha Excel padronizada e pronta para uso analítico.

### Exemplo de Conversão

Entrada (PDF):
```
01/01/2025   12   1   Pagamento fornecedor X  10.000,00  0,00  10.000,00C
02/01/2025   12   2   Recebimento cliente Y    0,00     3.500,00  6.500,00D
```

Saída (Excel):

| Dt. Movto | Lote | Lanç | Histórico | Débito | Crédito | Saldo Acum |
|------------|-------|-------|------------|----------|-----------|-------------|
| 01/01/2025 | 12 | 1 | Pagamento fornecedor X | 10.000,00 | 0,00 | 10.000,00C |
| 02/01/2025 | 12 | 2 | Recebimento cliente Y | 0,00 | 3.500,00 | 6.500,00D |

---

## Estrutura do Projeto

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

## Roadmap

- [x] Implementação inicial do parser e CLI  
- [x] Geração de Excel com `pandas` e `openpyxl`  
- [ ] Suporte a múltiplos arquivos PDF por lote  
- [ ] Exportação opcional em `.parquet`  
- [ ] Empacotamento para instalação via `pip`  

---

## Contribuindo

1. Faça um fork do repositório  
2. Crie uma branch (`git checkout -b feature/nova-feature`)  
3. Realize as modificações e commits  
4. Envie o pull request com uma breve descrição da melhoria  

Mais informações em [`CONTRIBUTING.md`](CONTRIBUTING.md)

---

## Licença

Distribuído sob a licença **MIT**.  
Consulte o arquivo [`LICENSE`](LICENSE) para mais informações.

---

## Autoria

Desenvolvido por **Suelen Farias**.  
Projeto aberto para colaboração e aprimoramento contínuo.
