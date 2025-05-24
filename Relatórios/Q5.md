# Relatório Q5 — Análise de Compatibilidade entre Extensões e Conteúdo Real dos Arquivos

## 1. Introdução

O objetivo desta análise foi verificar se as **extensões dos arquivos** encontrados na pasta `Exame` condizem com seu **conteúdo real**. A verificação foi feita por três métodos principais:

1. **Metadados (`stat`)** — verificação das datas de criação, acesso e modificação.  
2. **Comando `file`** — identifica o tipo real do arquivo pela estrutura interna.  
3. **Magic Numbers (`xxd`/`hexdump`)** — validação dos primeiros bytes do arquivo.

---

## 2. Resultados Obtidos

| Arquivo       | Extensão | Identificado por `file`                          | Magic Number            | Compatível |
|---------------|----------|--------------------------------------------------|--------------------------|------------|
| Depositos.png | .png     | Composite Document File (MS Office OLE2)         | `d0 cf 11 e0 a1 b1 1a e1` | ❌ Não     |
| export.csv    | .csv     | JavaScript source / Unicode text (<!DOCTYPE)     | `3c 21 44 4f 43 54`       | ❌ Não     |
| mpv32.bin     | .bin     | PDF document (version 1.4)                       | `25 50 44 46`            | ❌ Não     |
| Photo.jpg     | .jpg     | Unicode text                                     | `49 73 73 6f` (“Isso”)    | ❌ Não     |
| Setup.exe     | .exe     | PNG image data (960x720, RGBA)                   | `89 50 4e 47`            | ❌ Não     |

---

## 3. Análise dos Resultados

Todos os arquivos analisados apresentam **incompatibilidade entre a extensão e o conteúdo real**, o que pode indicar:

- **Ocultação deliberada**: arquivos renomeados para despistar análises.
- **Erro humano**: salvamento incorreto de extensões.
- **Manipulação maliciosa**: tentativa de disfarçar evidências (ex: documentos financeiros salvos como `.png`).

A verificação por **Magic Numbers** mostrou-se eficaz para autenticar o tipo real dos arquivos.

---

## 4. Conclusão

A análise confirma que **nenhum dos arquivos possui uma extensão condizente com seu conteúdo real**. Isso reforça a necessidade do uso de ferramentas como `file`, `xxd` e `hexdump` em investigações forenses para identificação de fraudes.

---

### 🔍 Próximos Passos Recomendados

- Abrir os arquivos em ambiente seguro para análise aprofundada do conteúdo.
- Investigar metadados embutidos para rastrear origem e histórico.
- Utilizar ferramentas como **Autopsy** ou **Plaso** para criar uma timeline de eventos.

