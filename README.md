# Estudos-SO--Ubuntu

Documentação da minha jornada autônoma estudando sistemas operacionais com Ubuntu Linux.

---

## 📖 O que aconteceu

Meu sistema Ubuntu estava apresentando problemas:

- O **Docker** não iniciava porque o serviço não estava instalado corretamente.
- O **libvirt** não tinha o arquivo de configuração necessário.
- O **Canonical Livepatch** falhava em cada inicialização.
- O serviço **casper-md5check**, usado apenas na instalação, continuava ativo sem necessidade.
- O kernel mostrava mensagens sobre o módulo **pcspkr**, que não era útil.

Em resumo: havia **serviços quebrados e pacotes inúteis** atrapalhando o funcionamento do sistema.

---

## 🔧 Como eu consertei

Resolvi cada problema de forma prática:

- Removi o módulo **pcspkr** e bloqueei para não aparecer mais.
- Reinstalei o **Docker** e habilitei o serviço.
- Reinstalei o **libvirt** e recriei sua configuração.
- Removi o **Canonical Livepatch** e limpei os resíduos.
- Desativei o serviço **casper-md5check**.
- Atualizei o sistema e limpei pacotes antigos com `apt update`, `apt upgrade`, `apt autoremove` e `apt clean`.
- Resetei falhas antigas no **systemd** para deixar o sistema limpo.

---

## ✅ Resultado

- O comando `systemctl --failed` mostrou **0 falhas**.
- Docker e libvirt voltaram a funcionar normalmente.
- O Livepatch foi removido com sucesso.
- O sistema ficou atualizado, limpo e estável.

---

## 📚 Tecnologias Utilizadas

- **Ubuntu Linux**
- **Docker**
- **Libvirt**
- **Systemd**

---

## 🎓 O que aprendi

Este projeto documenta a importância de:
- Monitorar serviços do sistema
- Limpar pacotes desnecessários
- Manter o sistema atualizado
- Resolver problemas de forma sistemática

---

## 📝 Licença

Este repositório é para fins educacionais.

