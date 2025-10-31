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

Script em Python que lê relatórios de Razão Contábil em PDF e exporta os lançamentos de forma **estruturada em Excel**, mantendo colunas padronizadas como:

| Dt. Movto | Lote | Lanç | Histórico | Débito | Crédito | Saldo Acum |
|------------|-------|-------|------------|----------|-----------|-------------|
| 01/01/2025 | 12 | 1 | Pagamento de fornecedor | 10.000,00 | 0,00 | 10.000,00C |
