[Documentación oficial](https://daringfireball.net/projects/markdown/syntax)

>    Markdown es usada para escribir para la web
 >  No es un reemplazo de HTML. Su sintaxis es pequeña. La idea no es hacer una sintaxis más fácil ded insertar HTML tags. Su idea es de hacerlo fácil de leer, escribir y editar prosa.
>   HTML es un formato de publicación, mientras que Markdown es de formato. 

Si se quiere escribir algo de HTML, usar simplemente la sintaxis de HTML


Una tabla, usa HTML tags y listo
## Tablas
Se pueden crear con sintaxis HTML

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

O con sintaxis markdown
```
| Syntax      | Description |
| :---------- | :---------: |
| Header      | Title       |
| Paragraph   | Text        |

Para decir si tienen que estar a la izquierda, derecha o al medio:
:----- (izquierda)
:----: (medio)
-----: (derecha)
```

| Syntax    | Description |
| --------- | ----------- |
| Header    | Title       |
| Paragraph | Text        |

## Caracteres especiales
Para generar caracteres especiales, usar &. Acá hay un listado de típicos usos:
&copy;
&amp;
&lt;
&#124;
lorem &nbsp; ipsum: agrega un espacio
lorem &ensp; ipsum: agrega 2 espacios
lorem &emsp; ipsum: agrega 3 espacios

## Headers

Hay 2 maneras:

This is an H1
==============

This is an H2
---------------------

Su ventaja es que permite cerrar lo de abajo, sin problemas

La otra manera es con:

# This is an H1
## This is an H2
### This is an H3

#### This is an H4

Y asi sucesivamente...

## Blockquotes

Se crean usando *&lt;*

> Como decía Fangio, carrera no se gana en la última curva, sino cuando baja la bandera
> Alfaro 20XX

Pueden tener dentro otros elementos de markdown

## Listas

### Listas sin orden

Se crean usando: +, -, *
+ Coca cola
+ Fanta
+ Sprite
+ Agua

### Listas con orden

Se crean usando números seguidos de un punto X.

1. Agua
2. Coca Cola
3. Fanta
4. Sprite

No hace falta que tengan el número en orden.


## Code blocks

Se crean usando ` Tres ``` ` Y se terminan de la misma forma o con 1 solo backticks
```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

Si querés agregar highlights, podes agregar el tipo que es al principio, en este caso JSON

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

## Horizontal rules

Para crear un `<hr />`, se usan 3 astericos, lineas bajas o lineas bajas
`* * * `

*****

`----`

------

`_____`
_________

## Énfasis


_single underscores_ 

**double asterisks**

__double underscores__
