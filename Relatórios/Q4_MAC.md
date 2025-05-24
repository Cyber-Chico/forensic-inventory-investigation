# Relatório Q4 — Análise de Tempos MAC

## 1. Introdução

Este relatório apresenta a análise dos arquivos encontrados na pasta `Exame` dentro da imagem forense `Chall_Pos_Tech_Img1.dd`, com foco nos tempos **M** (Modification), **A** (Access) e **C** (Change).

---

## 2. Procedimento Utilizado

1. **Montagem da imagem forense**:
```bash
mount -o loop,ro Chall_Pos_Tech_Img1.dd /mnt/imagem/
```

2. **Listagem dos arquivos**:
```bash
ls -lah /mnt/imagem/Exame
```

3. **Consulta dos tempos MAC**:
```bash
stat /mnt/imagem/Exame/*
```

---

## 3. O que são os tempos M, A e C?

- **M (Modification)** – Última vez que o conteúdo do arquivo foi alterado.  
- **A (Access)** – Última vez que o arquivo foi acessado (lido).  
- **C (Change)** – Última modificação nos metadados (como permissões, nome ou local).

---

## 4. Tabela de Análise dos Arquivos

| # | Nome do Arquivo | Extensão | Modification (M)       | Access (A)               | Change (C)               |
|---|------------------|----------|-------------------------|--------------------------|--------------------------|
| 1 | Depositos        | png      | 2023-06-23 16:12:04     | 2023-07-04 21:00:00      | 2022-06-23 16:12:04      |
| 2 | export           | csv      | 2022-07-18 14:32:58     | 2023-07-04 21:00:00      | 2022-07-18 14:32:58      |
| 3 | mpv32            | bin      | 2022-07-18 14:29:34     | 2023-07-04 21:00:00      | 2022-07-18 14:29:34      |
| 4 | Photo            | jpg      | 2022-07-04 16:56:22     | 2023-07-04 21:00:00      | 2022-07-04 16:56:22      |
| 5 | Setup            | exe      | 2022-07-06 15:55:42     | 2023-07-04 21:00:00      | 2022-07-06 15:55:42      |

---

## 5. Conclusão

A análise revelou que todos os arquivos possuem um **Change time (C)** idêntico ou muito próximo, sugerindo que foram copiados ou restaurados ao mesmo tempo.  
O **Access time (A)** indica leitura recente (04/07/2023), provavelmente durante alguma interação do sistema ou acesso pelo investigado.  
O **Modification time (M)** varia, apontando alterações feitas antes da cópia dos arquivos.

🔍 Ferramentas como **Plaso** e **Autopsy** poderiam complementar esta análise com uma linha do tempo detalhada dos eventos.
