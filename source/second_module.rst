This is second module
======================


| This module was written in .rst
| you can explore all features of reStructuredTex

    *a little tip: read the* docs_.

    .. _docs: https://docutils.sourceforge.io/rst.html



| italic : *aqui está um texto em italico*
| bold : **aqui está um texto em negrito**

| for code samples.

``texto em código``

lists :
* este é o primeiro elemento de uma lista não indexada
* este é o segundo elemento

1. está é uma lista enumerada
2. está vendo

#. esta também é uma lista enumerada
#. com dois items também


 1. Primeiro elemento

   1.1 primeiro elemento da seção


| *quotes:*

| essas linhas são
| quebradas exatamente como está
| no arquivo fonte

Este texto é um texto normal o proximo texto será um exemplo de codigo::

        isto não é processado em nenhum lugar exceto se a identação é removida

normal text

Tables


+------------------------+------------+----------+----------+
| Header row, column 1   | Header 2   | Header 3 | Header 4 |
| (header rows optional) |            |          |          |
+========================+============+==========+==========+
| body row 1, column 1   | column 2   | column 3 | column 4 |
+------------------------+------------+----------+----------+
| body row 2             | ...        | ...      |          |
+------------------------+------------+----------+----------+

alternative (more simple) form

===== === =========
A     B    A and B
===== === =========
False  1   Olá leo
True   2    e aí
===== === =========

================
This is a title
================



Lorem ipsum [#f1]_ dolor sit amet ... [#f2]_

.. rubric:: Footnotes

.. [#f1] Text of the first footnote.
.. [#f2] Text of the second footnote.


.. |name| replace:: replacement *text*