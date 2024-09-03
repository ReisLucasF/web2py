
# Configuração do Web2py no Ubuntu 20.04 LTS

Este guia fornece instruções detalhadas para configurar o Web2py em um servidor Ubuntu 20.04 LTS. Seguindo esses passos, você instalará e configurará o Web2py, além de configurar um certificado SSL para garantir a segurança do servidor.

## Pré-requisitos

- **Sistema Operacional:** Ubuntu 20.04 LTS
- **Acesso Root ou Sudo:** As operações requerem privilégios de superusuário

## Passo 1: Atualizar e Atualizar Pacotes do Sistema

Primeiro, vamos garantir que todos os pacotes do sistema estejam atualizados.

```bash
sudo apt update
sudo apt upgrade -y
```

## Passo 2: Baixar o Script de Instalação do Web2py

Baixe o script necessário para configurar o Web2py no Ubuntu 20.04.

```bash
sudo wget https://raw.githubusercontent.com/ReisLucasF/web2py/main/scripts/setup-web2py-ubuntu-focal.sh
```

Ou 

```bash
sudo wget https://raw.githubusercontent.com/web2py/web2py/master/scripts/setup-web2py-ubuntu-focal.sh
```

## Passo 3: Tornar o Script Executável

Após o download do script, é necessário conceder permissões de execução.

```bash
sudo chmod +x setup-web2py-ubuntu-focal.sh
```

## Passo 4: Executar o Script de Instalação

Agora, execute o script para instalar e configurar o Web2py.

```bash
sudo ./setup-web2py-ubuntu-focal.sh
```

## Passo 5: Configuração do Certificado SSL

Para garantir que o site seja acessível de forma segura, instale o Certbot e configure um certificado SSL.

### Instalar o Certbot

```bash
sudo apt install certbot python3-certbot-apache
```

### Configurar o Firewall para SSL

Abra as portas 80 (HTTP) e 443 (HTTPS) no firewall.

```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw reload
```

### Reiniciar o Apache

Após ajustar as regras do firewall, reinicie o Apache para aplicar as mudanças.

```bash
sudo systemctl restart apache2
```

### Executar o Certbot para Configuração SSL

Por fim, execute o Certbot para obter e configurar o certificado SSL.

```bash
sudo certbot --apache
```

## Conclusão

Essa é uma versão ajustada de uso pessoal do framework desenvolvido pelo autor  [Massimo Di Pierro](https://github.com/web2py/web2py/)
Caso tenha alguma dúvida ou problema durante o processo de instalação, consulte a [documentação oficial do Web2py](http://www.web2py.com/book) ou procure ajuda na comunidade.

---

