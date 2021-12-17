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
# Aula 03 - At Rules
## Placeholder Selector (%) e Extend:  
- Reaproveitador de bloco estilos estáticos, forma de agrupar um estilo padrão que irá ser muito utilizado;  

```scss
	%no-decoration {
		text-decoration: none;
	}
	%u-decoration {	
		text-decoration: underline;
	}

	&__post-title{
		font-size: 12px;
		color: $purple;
		@extend %no-decoration;
		&:hover{
			@extend %u-decoration;
		}
	}
```
## Mixins e Include:  
- Reaproveitador de bloco estilos dinâmicos, forma de agrupar um estilo padrão que irá ser muito utilizado, porém pode receber parâmetros;  
```scss
@mixin reset-list{
	margin: 0;
	padding: 0;
	list-style: none;
}

&__posts{
	@include reset-list;
}

@mixin flx($property, $jty-cnt){
	display: flex;
	//Variável
	#{$property}: $jty-cnt;
}
.breadcrumb{
	@include flx(justify-content, center);
	align-itens: center;
}
```
## Media queries e mixins:  
- Para uma melhor organização e facilidade de manutenção, usa-se mixins para compor os media queries;  
```scss
//mobile
@mixin for-phone-only{
	//@content serve para colocar o conteúdo que será enviado em um determinado lugar;
	@media (max-width: 767.98px) { @content; }
}
//tablet
@mixin for-tablet-only{
	@media (min-width: 768px) and (max-width: 1199.98px) { @content; }
}
//desktop
@mixin for-desktop-only{
	@media (min-width: 1200px){ @content ;}
}

//Usando as media queries
.header{
	.menu{
		&__list{
			display: flex;
			justify-content: center;
			@include for-phone-only{
				width: 90%;
				padding: 15px 0; 
				flex-wrap: wrap;
			}
			@include for-tablet-only{
				width: 80%;
				padding; 20px 0;
			}
			@include for-desktop-only{
				width: 80%;
				padding; 20px 0;				
			}
		}
	}
}
```
## Function  
- Uma função;  
- Modificar rem em px usando função e mixin:  
```scss
@function calculateRem($size){
	@return $size / 16px * 1rem;
}
@mixin fontSize($size){
	font-size: calculateRem($size); //chama a função
}

.footer{
	&__txt{
		margin: auto;
		@include fontSize(14px); //chama o mixin para usar a função
	}
}
```
Ex:
```scss
//$cor: obrigatório, $tam: se não for passado o valor, será 10px
@function funcao($cor, $tam: 10px){}
```
## Import:  
- Importar arquivos scss, é recomendação que os arquivos importados sejam renomeados com um "_" na frente: _header.scss  
```scss
@import 'header', 'footer';
```