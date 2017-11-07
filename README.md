# Marble Guideline

**Um guideline bem simples para se escrever CSS de forma escalável e de fácil manutenção.**

## CSS Structure

A estrutura do **Marble** é separada em **5** grupos, são eles:

* Components (componentes customizados)
* Elements (elementos padrão do html)
* Generic (reset, normalize, box-sizing)
* Settings (variáveis em geral)
* Tools (`functions` e `mixins`)

## Formatação

Seguimos os padrões do [cssguilen.es](https://cssguidelin.es/). Nosso objetivo é menter um código simples e limpo, ao qual qualquer pessoa poderá contribuir e dar manutenção.

De maneira geral, utilizamos as seguintes formatações:

* dois espaços de indentação, não é tab
* coluna com tamanho de 80 caracteres
* CSS de multiplas linhas
* utilização de espaços em branco para separar blocos de código
* uso de multiplos arquivos, cada contexto deve ser separado por arquivo
* comentários!

#### Espaços em branco = Legibilidade

Aqui vão algumas formatações a serem seguidas para que possamos ter uma melhor leitura do código:

* **uma linha** para regras de bastante relacionadas
* **duas linhas** para regras não tanto relacionadas
* **cinco linhas** para regras não relacionadas

```
.c-topbar {
  background: $secondary;
}

  .c-topbar .logo {
    height: base(6);
    width: base(6);
  }
  
  
  .c-topbar .menu {
    padding: base(1) 0;
  }
	
    .c-topbar .menu .link {
      color: rgba($primary, 0.8);
    }





.link {
  color: inherit;
  text-decoration: none;
}
```

## Sintaxe

Para um elemento/componente de UI mais complexo, aqueles que possuem várias classes ou que possuem outros elementos dentro dele, preferímos utilizar a convenção de nomenclatura do [RSCSS](http://rscss.io/css-structure.html).

```
.c-topbar {
  .link { /* ... */ }
  .logo { /* ... */ }
  .menu { /* ... */ }

  // variants
  -small { /* ... */ }
  -large { /* ... */ }
}
```

## Tipografia e rítmo vertical

Para nós, a tipografia é muito importante. Foi por isso que a separamos um local especial em `settings`, neste ambiente definimos tudo sobre este cara.

No `settings.typography` você irá encontrar os headings e os demais elementos de texto.

Todo nosso `line-height` é baseado em `baseline`. O que nos garante o rítmo vertical e nos mantém longe de números mágicos. Todos elementos e componentes do **Marble** respeitam a `baseline`.

Mas o que é `baseline`? É simples, `baseline` é nossa unidade para o rítmo vertical. Aqui utilizamos `6px`. Você pode encontrar esta definição no arquivo `settings.core`.

Também utilizamos a `baseline` para definir espaçamentos horizontais para `padding` e `margin`.

Uma vez que temos estes caras bem amarradinhos, nós podemos garantir que o rítmo vertical será respeitado e o layout vai ser apresentado corretamente.

Para atribuir um tamanho, padding ou margin, respeitando a `baseline`, você deve usar a função `base`:

```
.foo {
  padding: base(2) base(4);
}
```

O output será:

```
.foo {
  padding: 12px 24px;
}
```