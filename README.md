# DeployLaravel
Deploy de aplicação laravel no Hostinger/Weblink

1. Acessar painel administrativo.
2. Configurar o php.
3. Configurar o banco de dados.
4. Habilitar acesso SSH.
5. Abrir terminal e digitar os comandos abaixo.

Caso não tenho o serviço de SSH instalado.</br></br>
```
sudo apt-get install openssh-server
```

Para startar o serviço.</br></br>
```
sudo service ssh start`
```

6. Digite o comando abaixo substituido onde necessário.</br></br>
```
ssh nomeusuario@ip-remoto -p numeroporta
```

Após este comando o servidor irá solicitar sua senha.

7. Verifique as pastas com o comando ls do linux.
8. Você verá duas pastas `domains` e `public_html`
9. Acesse a pasta `domains`.</br></br>
```
cd domains`
```

10. Você verá seus dominios disponíveis.
11. Acesse a pasta do dominio que deseja usar.</br></br>
```
cd meu-dominio
```

12. Clone o resitorio do github para a pasta.</br></br>
```
git clone repositorio-do-github
```

13. Acesse a pasta do repositorio clonado.</br></br>
```
cd meu-site
```

14. Cria uma copia do arquivo .env.example.</br></br>
```
cp .env.example .env
```

15. Abra o arquivo .env criado.</br></br>
```
vim .env
```

16. Altere as linhas necessárias.</br></br>
```
APP_NAME=nome do projeto
APP_ENV=production
APP_DEBUG=false
APP_URL=http://meu-dominio
APP_DEBUG=false
DB_DATABASE=nome do banco gerado no painel
DB_USERNAME=nome de usuário gerado no painel
DB_PASSWORD=senha criada no painel
```

Saia do editor e salve as alterações.</br></br>

17. Instale todas as dependências do laravel.</br></br>
```
composer install --no-dev
```

18. Faça a migração de todas as tabelas do banco.</br></br>
```
php artisan migrate
```
Você será perguntado se realmente deseja fazer a migração em abiente de produção</br>
Confirme a operação</br></br>

19. Defina a APP_KEY do arquivo .env .</br></br>
```
php artisan key:generate
```

20. Volte para a pasta anteriorpara visualizar a pasta `meu-site` e a `public_html` .</br></br>
```
cd ..
```

21. Remova a pasta public_html e todos os seus arquivos.</br></br>
```
rm -Rf public_html
```

22. Agora crie um link simbólido para seu projeto.</br></br>
```
ln -s meu-site/public/ public_html
```

Com isso você ja irá conseguir acessar seu site...
