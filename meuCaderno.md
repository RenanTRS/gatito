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

# Aula 2: Regras de estilo e sintaxe  
## Nesting (Agrupamento) e Parent Selector &: 
```scss
header{
	font-family: Arial, sans-serif;

	&__logo{
		text-align: center;
	}
	.menu{
		&:not(:last-child)::after{
			content: "";
			position: absolute;
			top: 0;
			bottom: 0;
			.
			.
			.
		}
	}
}
```
- Com sass é possível colocar as classes dos seus filhos dentro, ajuda na organização do código, se as classes estiverem no formato BEM, e possível utilizar o & para deixar o código mais limpo;  

## Estilizando componentes da página:  
### interpolação:  
- Semelhante ao ${variavel} do js, no sass é #{$vairavel}
```scss
	$img-width: 45%;

	&__img{
		width: $img-width;
	}
	&__txt{
		width: calc(100% - #{$img-width});
	}
```