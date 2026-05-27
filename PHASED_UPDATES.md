# 🐧 Como Forçar Atualizações Retidas por Faseamento (Phased Updates) no Ubuntu

Ao gerenciar pacotes no Ubuntu através do terminal (`apt`), é comum se deparar com a mensagem informando que alguns pacotes foram retidos e não foram atualizados devido ao recurso de **faseamento (phasing)**.

Este documento explica brevemente o motivo desse comportamento e fornece os comandos necessários para forçar a instalação imediata desses pacotes.

---

## 🔍 Entendendo o Problema: O que é o Faseamento?

O **faseamento de atualizações** é um mecanismo de segurança do Ubuntu. Quando uma nova atualização é lançada, ela não é liberada para 100% dos usuários ao mesmo tempo. O sistema envia a atualização em etapas (porcentagens progressivas) para detectar possíveis bugs e evitar que falhas quebrem o sistema de todos os usuários simultaneamente.

Embora seja uma medida de segurança útil, existem cenários onde você precisa daquela instalação ou correção **na hora**, sem esperar o cronograma automático do sistema.

---

## 🛠️ Solução: Comandos Utilizados

Para contornar o bloqueio e forçar a atualização imediata na marra, os seguintes passos foram executados no terminal como usuário administrador (`root`):

### 1. Sincronizar os Repositórios

Antes de tudo, atualize a lista de pacotes locais para garantir que o sistema conhece as versões mais recentes disponíveis:

```bash
apt update
```

### 2. Forçar a Atualização Passando por Cima do Faseamento

Para ignorar a trava de segurança do faseamento e obrigar o gerenciador de pacotes a instalar as atualizações retidas (`gir1.2-mutter-10`, `libmutter-10-0`, `mutter-common`, etc.), utilize a flag de configuração `-o` diretamente no comando `upgrade`:

```bash
apt upgrade -o APT::Get::Always-Include-Phased-Updates=true -y
```

### 💡 Resultado Esperado

O parâmetro acima força o `apt` a tratar os pacotes em faseamento como atualizações normais e obrigatórias. Ao rodar um novo `apt update` após o procedimento, você receberá a mensagem definitiva de sucesso:

> **"Todos os pacotes estão atualizados."**

---

## 📌 Resumo Rápido

| Comando | Função |
|---------|--------|
| `apt update` | Sincroniza repositórios |
| `apt upgrade -o APT::Get::Always-Include-Phased-Updates=true -y` | Força instalação de pacotes em faseamento |

---

## ⚠️ Aviso Importante

- Use este comando com cuidado e apenas quando tiver **certeza** de que precisa das atualizações imediatamente
- O faseamento existe por uma razão: proteger o sistema
- Sempre faça backup antes de forçar atualizações críticas
