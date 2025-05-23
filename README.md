# forensic-inventory-investigation

Projeto forense desenvolvido na pós-graduação em Cibersegurança. Consiste no levantamento e análise de mídias digitais, com inventário completo dos arquivos, validação por hash e identificação de evidências relevantes.

## 🕵️‍♂️ Contexto

Este projeto simula um cenário real de atuação forense, com base no desafio proposto na disciplina de Fundamentos de Forense Digital. Foi realizado o cumprimento de mandado de busca fictício na empresa ATMOSIGMA LTDA, com análise de diversos dispositivos apreendidos.

## 🔍 Tópicos Abordados

- Cadeia de custódia (modelo NIST)
- Criação e verificação de cópias forenses (`dd`)
- Sanitização de mídias (pendrives, SSDs, partições)
- Análise de arquivos via `mount` e navegação forense
- Verificação de integridade com Magical Numbers
- Desafios da perícia em SSDs modernos
- Investigação de arquivos protegidos (questão bônus)

## 🧪 Ferramentas Utilizadas

- Linux (linha de comando)
- `dd`, `dcfldd`, `sha256sum`
- Autopsy (opcional)
- `file`, `hexdump`, `strings`
- Gnome Disk Utility / `wipefs` / `mkfs`
- Navegadores de arquivos e terminais

## 📁 Estrutura do Projeto

```
projeto/
├── imagens_forenses/
│   ├── Chall_Pos_Tech_Ori.dd
│   ├── Chall_Pos_Tech_Img1.dd
│   └── Chall_Pos_Tech_Img2.dd
├── relatorios/
│   ├── relatorio_completo.pdf
│   └── prints_etapas.png
├── tabelas/
│   └── tempos_MAC.csv
└── bonus/
    └── planilha_bonus_desencriptada.xlsx
```

## 📝 Questões Respondidas

O projeto responde às 6 questões centrais do desafio, além da questão bônus opcional:

| Questão | Tema                                                             | Status     |
|--------:|------------------------------------------------------------------|------------|
| Q1      | Cadeia de custódia e modelo NIST                                 | ✅ Concluído |
| Q2      | Verificação de integridade e tipo de filesystem                  | ✅ Concluído |
| Q3      | Sanitização de mídia e validação                                | ✅ Concluído |
| Q4      | Extração de dados com M/A/C time                                | ✅ Concluído |
| Q5      | Verificação de conteúdo vs extensão com magic numbers           | ✅ Concluído |
| Q6      | Desafios de análise forense em SSDs                             | ✅ Concluído |
| Bônus   | Acesso a arquivo protegido em local suspeito                     | ✅ Concluído |

## 📄 Relatório

O relatório detalhado pode ser acessado na pasta `relatorios/`.

## 🧠 Autor

Francisco Carlos de Oliveira Júnior
Pós-graduação em Cibersegurança – Blue Team Operations
