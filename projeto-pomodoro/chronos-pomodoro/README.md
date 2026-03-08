# 🎨 Estruturando o Tema e CSS Global da Aplicação

Chegou a hora de sairmos dos exemplos básicos de "Hello World" e começarmos a
montar a estrutura real da nossa aplicação! Nesta aula, preparamos a fundação do
nosso visual criando um sistema de cores com variáveis CSS e aplicando um
_Reset_ global para padronizar o layout.

---

## 🌈 1. O Sistema de Variáveis (Design System)

No arquivo `src/styles/theme.css`, vamos colar a nossa paleta de cores. Como a
aplicação terá um Modo Claro e um Modo Escuro (começaremos pelo escuro),
precisamos de uma estrutura sólida de variáveis.

### Como nossas variáveis estão organizadas?

- **Tons de Cinza (`--gray-100` a `--gray-900`):** Usados para fundos e
  elementos de interface. O `100` é o mais claro e o `900` é o mais escuro.
- **Cor Primária:** Nosso tom de verde principal (`--primary`).
- **Cores de Alerta (Feedbacks):** \* `--success` (Verde: operação bem-sucedida)
  - `--warning` (Amarelo: atenção/aviso)
  - `--error` (Vermelho: falha/erro)
  - `--info` (Azul: informação neutra)
- **Cores de Texto Baseadas no Fundo:** Criamos variáveis específicas para
  textos que ficam _sobre_ fundos coloridos (ex: `text-on-primary`). Isso
  garante que, mesmo quando mudarmos o tema de claro para escuro, o texto dentro
  de um botão verde continue legível.
- **Textos Gerais:** `--text-default` (cor principal da leitura), `--text-muted`
  (textos secundários/apagados) e cores para elementos desativados (`disabled`).

---

## 🧹 2. Reset de CSS e Configuração do `rem`

No arquivo `src/styles/global.css`, removemos os testes da aula anterior e
configuramos a base do nosso projeto.

### O Reset Básico

Zeramos as margens e preenchimentos que o navegador aplica por padrão e
ajustamos o modelo de caixa:

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

**O Truque do `{62.5% }`(Unidade REM)** O navegador, por padrão, tem o tamanho
de fonte de `16px`. Trabalhar com a unidade relativa `rem` é uma excelente
prática para acessibilidade e responsividade, mas calcular os valores de cabeça
pode ser chato (ex: 20px seria 1.25rem).

Para resolver isso, aplicamos um truque no `html`:

```css
html {
  font-size: 62.5%;
}
```

**O que isso faz?** Reduz a fonte base de `16px` para `10px` (pois 62.5% de 16 =
10). Agora, a matemática fica super simples: basta dividir o valor em pixels por
10 e trocar o ponto!

- Quer 16px? Escreva 1.6rem.
- Quer 25px? Escreva 2.5rem.
- Quer 400px? Escreva 40rem.

## 📄 3. Estilizando o `body`

Ainda no `global.css`, aplicamos as configurações padrão para a nossa página
inteira, consumindo as variáveis que criamos no arquivo de tema:

```css
body {
  /* Tamanho base de 16px, graças ao truque do rem! */
  font-size: 1.6rem;

  /* Fonte padrão do sistema operacional do usuário */
  font-family:
    -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial,
    sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';

  /* Aplicando nossas variáveis do tema escuro */
  background-color: var(--gray-900);
  color: var(--text-default);
}
```

## 🔜 Próximos Passos

Com o nosso CSS Global e Tema configurados, agora temos o fundo escuro e o texto
claro aplicados corretamente na tela.

Na próxima aula, voltaremos ao nosso componente `<Heading />`. Vamos estilizá-lo
e prepará-lo para ser flexível, pois em algumas páginas (como a de "Histórico")
ele precisará renderizar um botão extra ao seu lado!
