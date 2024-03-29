---
description: Template Method
---

# Шаблонный метод

## Назначение

Паттерн шаблонный метод (Template Method) представляет из себя класс, который позволяет собирать метод из алгоритмов на основе этапов и варьировать каждый из этих алгоритмов.

При этом задачей самого шаблонного метода становится передача данных после выполнения определённого этапа на следующий этап.

## Решаемые задачи

* управление расширениями подклассов

{% hint style="info" %}
Можно определить шаблонный метод так, что он будет вызывать операции-зацепки (hooks) в определенных местах программы, разрешив тем самым расширение только в этих местах.
{% endhint %}

* избавление от дублирования кода методом вычленения и локализации в одном классе поведения, общего для всех подклассов

{% hint style="info" %}
Сначала идентифицируются различия в существующем коде, а затем они выносятся в отдельные операции (методы или функции). В конечном итоге различающиеся фрагменты кода заменяются шаблонным методом, из которого вызываются новые операции.
{% endhint %}

* необходимость использовать одни и те же части алгоритма повторно, оставляя возможность изменять специфическое поведение в разных подклассах

## Преимущества

* позволяет избежать дублирования кода
* облегчается замена алгоритмов и методов без внесения изменений в основную структуру кода
* упрощается понимание и поддержка кода за счет разделения алгоритмов на более мелкие этапы
* возможность управления расширениями подклассов

## Недостатки

* внесение изменений в общую структуру алгоритма может потребовать соответствующих изменений во всех подклассах.
* при значительном увеличении числа этапов алгоритма класс может стать слишком сложным и трудным для поддержки и понимания
* множественные шаги алгоритма, каждый из которых требует изменений в отдельном подклассе, могут привести к созданию большого количества классов-наследников

## Связь с другими паттернами

* [Фабричный метод](../../creationals-patterns/factory-method/): часто вызывается из шаблонных методах.
* [Стратегия](../strategy/): шаблонные методы применяют наследование для модификации части алгоритма. Стратегии используют делегирование для модификации алгоритма в целом.
* [Декоратор](../../structural-patterns/dekorator/): шаблонный метод может быть использован вместе с паттерном декоратор для добавления дополнительного поведения внутри шагов алгоритма. Декораторы могут быть применены к определенным шагам алгоритма, чтобы модифицировать их поведение без изменения самого шаблона метода.
* [Цепочка обязанностей](../chain-of-responsibility/): шаблонный метод может быть частью цепочки обязанностей, где каждый шаг алгоритма представляет отдельное звено в цепочке. Цепочка обязанностей позволяет разделить обработку запросов на разные уровни и динамически определить, какой шаг должен обработать конкретный запрос.
