# Phishing para captura de senhas do Facebook

Desafio prático da DIO — trilha de Cybersecurity. Uso da ferramenta **setoolkit** (Social-Engineer Toolkit) no Kali Linux para criar uma página falsa de login do Facebook e capturar credenciais em ambiente de laboratório.

## Ferramentas
- Kali Linux (VM no VirtualBox)
- setoolkit

## Configurando o Phishing no Kali Linux

- **Acesso root:** `sudo su` (digitar a senha do kali)
- **Iniciando o setoolkit:** `setoolkit`
- **Tipo de ataque:** Social Engineering Attacks → opção `1`
- **Vetor de ataque:** Website Attack Vectors → opção `2`
- **Método de ataque:** Credential Harvester Attack Method → opção `3`
- **Método de clone:** Site Cloner → opção `2`
- **IP do servidor:** IP da minha máquina Kali (descobrir com `ip a`)
- **URL para clonar:** `http://www.facebook.com`

Detalhe importante: precisei mudar a rede da VM no VirtualBox de NAT para **Bridge Adapter** (Machine → Settings → Network) e reiniciar a VM, senão a página falsa não fica acessível a partir do meu Windows (host).

## Teste

Abri uma aba anônima no navegador do Windows (host) e acessei `http://<IP-do-Kali>`. A página clonada do Facebook carregou igualzinha. Digitei as credenciais de teste:

- Email: `joao@gmail.com`
- Senha: `passwd`

Cliquei em Entrar e a página redirecionou pro Facebook real (glitch normal do clone, o leigo não percebe).

## Resultados

No terminal do Kali, o harvester mostrou o POST em vermelho com o email e a senha capturados:

```text
POSSIBLE USERNAME FIELD FOUND: email=joao@gmail.com
POSSIBLE PASSWORD FIELD FOUND: pass=passwd  - ***
```

## Prints

| Etapa | Imagem |
|-------|--------|
| 1. Página falsa do Facebook carregando no Windows | `images/01-fake-facebook.png` |
| 2. Menu do setoolkit — Social Engineering Attacks | `images/02-menu-social-eng.png` |
| 3. Menu do setoolkit — Website Attack Vectors | `images/03-menu-website-attack.png` |
| 4. Menu do setoolkit — Credential Harvester | `images/04-menu-harvester.png` |
| 5. POST capturado no terminal do Kali | `images/05-post-capturado.png` |