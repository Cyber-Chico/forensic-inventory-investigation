# Relatório Bônus — Acesso a Planilha Protegida

## Introdução

Durante a análise da imagem de disco `Chall_Pos_Tech_Img1.dd`, proveniente de um caso fictício de fraude contábil na empresa ATMOSIGMA, foi solicitada a tarefa de acessar uma planilha protegida por senha localizada na pasta `Bonus`.

---

## 1. Montagem da Imagem de Disco

A imagem foi montada em um ambiente Linux (Kali) com o comando:

```bash
sudo mount -o loop Chall_Pos_Tech_Img1.dd /mnt
cd /mnt/Bonus
```

---

## 2. Identificação dos Arquivos

Foram localizados arquivos `.xls` e `.xlsx`, incluindo o alvo principal:  
**Planilha2.xlsx**

---

## 3. Busca pela Senha em Arquivos Binários

Utilizando a dica de que a senha estava em "lugar seguro", foi feita uma varredura com:

```bash
strings /mnt/Bonus/bin/binfile23 | grep -i "planilha" -n5
```

Este comando exibe a palavra-chave "planilha" e linhas antes/depois para contexto.

---

## 4. Descoberta da Senha

Na linha 703 foi localizada a referência ao arquivo `Planilha2.xlsx`, e na linha seguinte foi encontrado:

```
FLAGFIAP99
```

Inferindo-se que **FLAGFIAP99** era a senha da planilha.

---

## 5. Acesso à Planilha

A senha foi testada com sucesso utilizando **LibreOffice Calc**, resultando no acesso total à planilha `Planilha2.xlsx` com dados potencialmente relevantes para a investigação.

---

## Conclusão

A investigação demonstrou a importância do uso de comandos como `strings` e `grep` para localizar evidências escondidas em arquivos binários.  
Com a montagem adequada da imagem forense, foi possível **acessar informações críticas protegidas por senha** e registrar os resultados com sucesso.

