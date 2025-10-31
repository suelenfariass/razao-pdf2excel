# Razão PDF → Excel (Tabular)

Extrai lançamentos de um Razão em PDF (formatação comum no Brasil) para um Excel tabulado.

> **Stack:** `pandas`, `pdfplumber`, `openpyxl`

## Instalação

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

pip install -r requirements.txt
```

## Uso

```bash
python src/razao_pdf2xlsx.py --pdf "entrada.pdf" --out "out/razao.xlsx"
```

Opções úteis:

- `--sheet-name "lancamentos"`: nome da aba no Excel
- `--ignore "NOME DA SUA ENTIDADE"`: adiciona padrões de cabeçalho/rodapé a ignorar (pode repetir a flag)

Exemplo (Windows, com ^ para quebra de linha):

```bash
python src/razao_pdf2xlsx.py ^
  --pdf ".\examples\RAZAO_EXEMPLO.pdf" ^
  --out ".\out\razao_exemplo.xlsx" ^
  --ignore "Relatório Contábil" ^
  --ignore "Empresa XYZ S.A."
```

## Como funciona

- Identifica cada lançamento pelo padrão `DD/MM/AAAA  LOTE  LANC` em **qualquer** ponto da linha.
- Concatena continuações até o próximo lançamento.
- Extrai `Débito`, `Crédito` e `Saldo (C/D)` no **primeiro trio** encontrado no bloco.
- Entrega colunas: `Dt. Movto`, `Lote`, `Lanç`, `Histórico`, `Débito`, `Crédito`, `Saldo Acum`.

## Limitações & Dicas

- PDFs **escaneados** (imagem) precisam de OCR (ex.: Tesseract) **antes** da execução.
- Layouts muito customizados podem exigir ajustes em `START_RE` ou na lista de linhas a ignorar (`--ignore`).
- Ajuste `x_tolerance`/`y_tolerance` no `parse_pdf_anywhere` caso seu PDF tenha espaçamentos diferentes.

## Estrutura do repositório

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
└─ requirements.txt
```

## Privacidade

- O repositório **não** contém dados reais.
- Use `--ignore` para filtrar nomes próprios/headers específicos.
- Não versione arquivos gerados: veja `.gitignore`.

## Licença

MIT. Veja `LICENSE`.
