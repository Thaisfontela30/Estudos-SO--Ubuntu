# Estudos-SO--Ubuntu

Documentação da minha jornada autônoma estudando sistemas operacionais com Ubuntu Linux.

---

## 📚 Índice de Conteúdos

- [Consertando Serviços Quebrados](#consertando-serviços-quebrados)
- [Phased Updates (Faseamento de Atualizações)](#phased-updates)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [O que Aprendi](#o-que-aprendi)

---

## Consertando Serviços Quebrados

### 📖 O que aconteceu

Meu sistema Ubuntu estava apresentando problemas:

- O **Docker** não iniciava porque o serviço não estava instalado corretamente.
- O **libvirt** não tinha o arquivo de configuração necessário.
- O **Canonical Livepatch** falhava em cada inicialização.
- O serviço **casper-md5check**, usado apenas na instalação, continuava ativo sem necessidade.
- O kernel mostrava mensagens sobre o módulo **pcspkr**, que não era útil.

Em resumo: havia **serviços quebrados e pacotes inúteis** atrapalhando o funcionamento do sistema.

### 🔧 Como eu consertei

Resolvi cada problema de forma prática:

- Removi o módulo **pcspkr** e bloqueei para não aparecer mais.
- Reinstalei o **Docker** e habilitei o serviço.
- Reinstalei o **libvirt** e recriei sua configuração.
- Removi o **Canonical Livepatch** e limpei os resíduos.
- Desativei o serviço **casper-md5check**.
- Atualizei o sistema e limpei pacotes antigos com `apt update`, `apt upgrade`, `apt autoremove` e `apt clean`.
- Resetei falhas antigas no **systemd** para deixar o sistema limpo.

### ✅ Resultado

- O comando `systemctl --failed` mostrou **0 falhas**.
- Docker e libvirt voltaram a funcionar normalmente.
- O Livepatch foi removido com sucesso.
- O sistema ficou atualizado, limpo e estável.

---

## Phased Updates

### 🐧 Como Forçar Atualizações Retidas por Faseamento

Aprendi como contornar o mecanismo de segurança do Ubuntu que retém atualizações em faseamento (phased updates).

**Leia o guia completo:** [PHASED_UPDATES.md](./PHASED_UPDATES.md)

**Comando rápido:**
```bash
apt update
apt upgrade -o APT::Get::Always-Include-Phased-Updates=true -y
```

---

## 📚 Tecnologias Utilizadas

- **Ubuntu Linux**
- **Docker**
- **Libvirt**
- **Systemd**
- **APT** (Advanced Package Tool)

---

## 🎓 O que Aprendi

Este projeto documenta a importância de:

- Monitorar serviços do sistema e identificar falhas
- Limpar pacotes e serviços desnecessários
- Manter o sistema atualizado e estável
- Resolver problemas de forma sistemática
- Entender mecanismos de segurança do Ubuntu (como phased updates)
- Usar o terminal de forma eficiente para troubleshooting

---

## 📝 Licença

Este repositório é para fins educacionais.
