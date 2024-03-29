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
Полиморфизм – это очень мощный механизм, который позволяет модифицировать программу «не изменяя» написанный код, за счет добавления новых классов. Дословный перевод полиморфизма много форм. Синоним полиморфизма – безразличие, когда один и тот же код может работать с объектами разных классов (типов).
{% endhint %}

При модификации программы происходит подмена объектов одних классов на объекты других классов. Как правило в объектно-ориентированных языках это реализуется за счет передачи в методы ссылок (указателей) на базовые полиморфные классы или за счет интерфейсов. Так же подмена осуществляется на этапе компиляции при помощи обобщений (шаблонов).

Однако,  при использовании полиморфизма рано или поздно возникает необходимость создания конкретного объекта (сущности) конкретного типа. Для расширения, модификации или подмены сущности будет необходимо искать, где она создается и менять код. Это усложняет модификацию программы: увеличивается время модификации, понижается надежность программы, возникают проблемы с версионностью.

**Порождающие паттерны** – группа паттернов проектирования, которые берут на себя ответственность за логику создания объектов. Они позволяют нам не создавать в методах объекты конкретных классов, дают возможность принимать решение объекты каких классов нужно создавать при выполнении программы и лишний раз не создавать объекты заново, а использовать уже созданные.
