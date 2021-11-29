# Aula 1 - Primeiros passos;
### Instalação global 
```bash
sudo npm install -g sass
```
- Criar dois arquivos style.css e style.scss

### Executar o preprocessador e cria o arquivo de compilação **style.css.map**
```bash
sass style.scss:style.css
```

### Monitorar para atualizar o css automaticamente
```bash
sass --watch scss/style.scss:css/style.css
```

### Criar variável
```scss
$purple: #A050BE
$light-grey: #eaeaeb;
$dark-grey: #464646;

.header{
	color: $purple;
}
```

### Comentário:
"//" ou "/**/" comentários normais  
"///" comentário para documentação