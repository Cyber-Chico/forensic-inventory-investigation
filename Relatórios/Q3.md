# Relatório Q3 — Esterilização de Drive

## 1. Introdução

Este relatório descreve o procedimento de esterilização de um drive para assegurar que nenhum dado residual esteja presente antes da criação de uma nova imagem forense.  
A sanitização do dispositivo é essencial para garantir a integridade das análises subsequentes.

---

## 2. Ferramentas Utilizadas

Durante o processo de esterilização, foram utilizadas as seguintes ferramentas:

- **dd** – Para sobrescrever os dados do disco com zeros ou dados aleatórios  
- **dcfldd** – Versão aprimorada do dd, permitindo melhor controle do processo  
- **shred** – Para realizar múltiplas passagens e garantir a remoção segura dos dados  
- **blkdiscard** – Para apagar rapidamente SSDs sem desgaste excessivo  
- **nvme format** – Para formatação segura de SSDs NVMe  

---

## 3. Procedimento Realizado

1. **Identificação do dispositivo**  
   Comando: `lsblk` — lista os dispositivos de armazenamento disponíveis.

2. **Desmontagem do drive**  
   Caso o dispositivo estivesse montado:  
   `umount /dev/sdX` — para evitar problemas durante a sanitização.

3. **Sobrescrita dos dados**  
   - Para discos rígidos (HDD):  
     `dd if=/dev/zero of=/dev/sdX bs=1M status=progress`  
   - Para maior segurança:  
     `shred -n 3 -v /dev/sdX`  
   - Para SSDs:  
     `blkdiscard /dev/sdX`  
   - Para SSDs NVMe:  
     `nvme format /dev/nvme0n1`

---

## 4. Verificação da Sanitização

Para confirmar que a sanitização foi realizada com sucesso, foram utilizados os seguintes métodos:

- `hexdump -C /dev/sdX | head` — Verifica ausência de dados residuais  
- `blkdiscard -v /dev/sdX` — Confirma a liberação dos blocos  
- `lsblk -f /dev/sdX` — Confirma que não havia sistemas de arquivos remanescentes

---

## 5. Conclusão

O processo de esterilização do drive foi concluído com sucesso, garantindo que nenhum dado residual permaneceu no dispositivo antes de sua reutilização em análises forenses.
