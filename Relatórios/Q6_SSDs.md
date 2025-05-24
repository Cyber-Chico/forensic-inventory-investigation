# Relatório Q6 — Desafios Forenses na Análise de SSDs

## 1. Introdução

Os Solid-State Drives (SSDs) trouxeram avanços significativos no armazenamento digital, oferecendo alta velocidade e confiabilidade. No entanto, esses benefícios introduzem desafios substanciais para a **perícia forense computacional**, especialmente na **preservação e recuperação de evidências digitais**.

---

## 2. Mecanismos de Gerenciamento de Memória

- SSDs utilizam **Garbage Collection**: processo interno que reorganiza e limpa blocos de memória para manter o desempenho.  
- Esse processo pode **eliminar evidências digitais** prematuramente, dificultando a recuperação de arquivos excluídos.

---

## 3. Comando TRIM

- O **comando TRIM** permite que o sistema operacional informe ao SSD quais blocos de dados podem ser apagados.  
- Isso **remove os dados imediatamente**, o que torna a recuperação de arquivos excluídos **muito mais difícil** do que em HDDs tradicionais.  
- É uma das principais limitações em ambientes forenses modernos.

---

## 4. Criptografia e Segurança

- Muitos SSDs modernos contam com **criptografia embutida por hardware**.  
- Dispositivos com **auto-encryption** exigem autenticação e dificultam cópias forenses completas.  
- Sem acesso à chave de descriptografia, a análise pode ser **totalmente inviabilizada**.

---

## 5. Volatilidade dos Dados

- SSDs tendem a sobrescrever dados com mais frequência devido a algoritmos de otimização.  
- Arquivos apagados podem ser **rapidamente sobrescritos ou limpos**, reduzindo o tempo disponível para coleta de evidências.  
- **Tempo de retenção de dados** pode ser menor, principalmente em unidades desgastadas ou sem alimentação.

---

## 6. Conclusão

A análise forense de SSDs exige o uso de **ferramentas especializadas** e uma compreensão profunda dos mecanismos internos da tecnologia.  
Métodos tradicionais aplicados a discos rígidos podem ser **ineficientes ou ineficazes** em SSDs. A perícia digital moderna deve evoluir para acompanhar as particularidades desses dispositivos, adaptando suas práticas e adotando novas técnicas de preservação e extração de dados.

