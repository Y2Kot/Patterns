---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Порождающие паттерны

## Общее описание

{% hint style="info" %}
Полиморфизм – это очень мощный механизм, который позволяет модифицировать программу «не изменяя» написанный код, за счет добавления новых классов. Дословный перевод полиморфизма - много форм. Синоним полиморфизма – безразличие, когда один и тот же код может работать с объектами разных классов (типов).
{% endhint %}

> Тут мог быть анекдот про таксу

При модификации программы происходит подмена объектов одних классов на объекты других классов. Как правило, в объектно-ориентированных языках это реализуется за счет передачи в методы ссылок (указателей) на базовые полиморфные классы или за счет интерфейсов. При использовании обобщений (шаблонов) подстановка типов осуществляется на этапе компиляции.

При использовании полиморфизма рано или поздно возникает необходимость создания конкретного объекта (сущности) конкретного типа. Для расширения, модификации или подмены сущности будет необходимо найти все места, где создается объект, и изменить код. Такая модификация программы увеличивает время разработки, понижает надежность программы, приводит к проблемам с версионностью.

**Порождающие паттерны** – группа паттернов проектирования, которые&#x20;

* берут на себя ответственность за логику создания объектов,&#x20;
* позволяют нам не создавать в методах объекты конкретных классов,
* дают возможность принимать решение объекты каких классов нужно создавать при выполнении программы,
* дают возможность повторно использовать уже созданный объект.
