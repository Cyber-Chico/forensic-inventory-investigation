# Q2 — Verificação de Integridade e Análise Forense das Imagens

## 🔍 Introdução

Esta investigação forense teve como objetivo verificar se as imagens forenses extraídas de um disco original foram copiadas corretamente, identificar possíveis manipulações e recuperar dados excluídos.

---

## 🧪 Ferramentas Utilizadas

- Sleuth Kit (fls, istat, ifind, ffind, icat)
- `md5sum`, `sha1sum`, `sha256sum` (verificação de hash)
- `file` (identificação do sistema de arquivos)
- `foremost`, `photorec` (recuperação de arquivos deletados)
- `strings` (extração de conteúdo textual binário)

---

## 📊 Análise

### 3.1 Verificação de Integridade

Hashes comparativos entre original e cópias:

| Arquivo                  | md5sum                                 | sha1sum                                 | sha256sum                                 |
|--------------------------|----------------------------------------|------------------------------------------|--------------------------------------------|
| Ori.dd                   | `971d78306693c912a39a469f04ca9e73`     | `decc6091ddac5b588fb19af5e7cbd4f108643928` | `daebb6177cc66b7bd161c30a0b4587fc2a958d3b16887777452df9094df7f31` |
| Img1.dd                  | `02fa6531412aa0da2eecc37a5f7877a48c`   | `6772d971131a9327210467308455231cfd6dc5c5` | `c19ea59e0e65282f0ce50418bb76520bf3aad87b25eee4c27cb91212b58f1f` |
| Img2.dd                  | `d9a96946a67c7bd47bbce564d702eabae`   | `ecae8e826264093769d5cdadb6c6c9f3cb3eba24d` | `133c7d3fb85782eec7fe10a184c6389746e96581cd47d1e583d0def980ac7389` |

**Resultado:** Ambas as imagens são diferentes da original — indicando cópias incorretas ou manipuladas.

---

### 3.2 Sistema de Arquivos

| Imagem                 | Sistema de Arquivos |
|------------------------|---------------------|
| Original               | FAT16               |
| Img1.dd                | FAT16               |
| Img2.dd                | NTFS ❌             |

A imagem 2 foi modificada para NTFS, indicando possível tentativa de ocultação de dados.

---

### 3.3 Recuperação de Dados Excluídos

- Listagem de arquivos deletados com `fls -r -m / Chall_Pos_Tech_Img2.dd | grep deleted`
- Evidência de:
  - `DicaBonus.txt`
  - Pastas `Trash-1000/` e `$OrphanFiles/`
- `icat` recuperou parcialmente os arquivos deletados
- `foremost` e `photorec` identificaram fragmentos sobrescritos

---

### 3.4 Investigação sobre formatação NTFS

- `strings` revelou comandos `format` dentro da imagem NTFS
- `istat` mostrou que a raiz foi criada em 19/07/2022 — muito posterior ao conteúdo do sistema, indicando formatação recente e intencional

---

## ⚠️ Pontos Relevantes

- A imagem 1 foi mal copiada.
- A imagem 2 sofreu formatação NTFS (alteração grave).
- Alguns dados foram recuperados com ferramentas forenses.
- Sinais claros de manipulação digital com intenção de ocultar evidências.

---

## 🧠 Estratégia Forense

- **Validação de integridade** por hash
- **Comparativo temporal** com metadados
- **Busca por manipulações** (como formatação disfarçada)
- **Carving de arquivos** para tentar recuperação de artefatos

---

## 🔁 Recomendações Futuras

- Investigar fragmentos com técnicas mais avançadas
- Recuperar MFT com ferramentas especializadas
- Revisar arquivos parcialmente recuperados manualmente

---

## ✅ Conclusão

A análise revelou que houve **manipulação direta** das imagens forenses — com alteração de sistema de arquivos e tentativa de ocultação de dados. A cópia fiel do disco original não foi preservada, comprometendo a cadeia de integridade. Ainda assim, rastros digitais foram parcialmente resgatados.

