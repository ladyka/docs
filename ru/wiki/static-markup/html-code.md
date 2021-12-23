# Элементы HTML

## Теги {#html-tags}
Чтобы вставить на страницу элементы оформления, которые не предусмотрены разметкой Markdown, вы можете использовать в тексте теги HTML.

Например:

* ```html
  <p style="color: gray; font-weight: bold;">Текст серого цвета</p>
  ```
    {% cut "Как выглядит результат" %}

    ![](../../_assets/wiki/gray-text.png)

    {% endcut %}

* ```html
  <p style="border-width: 4px; border-style: double; border-color: orange;">Текст в рамке</p>
  ```

    {% cut "Как выглядит результат" %}

    ![](../../_assets/wiki/border-text.png)

    {% endcut %}

* ```html
  <table border="1">
    <tr><td>Значение 1</td><td>Значение 2</td></tr>
    <tr><td>Значение 3</td><td>Значение 4</td></tr>
  </table>
  ```

    {% cut "Как выглядит результат" %}

    ![](../../_assets/wiki/html-table.png)

    {% endcut %}

