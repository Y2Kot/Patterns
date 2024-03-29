---
description: Property
---

# Свойство

## Назначение

Паттерн свойство (Property) представляет собой объединение двух методов - получения и изменения значения, что позволяет обеспечить сохранение целостности доступа к данным объекта.

## Решаемые задачи

* инкапсуляция данных: паттерн Свойство помогает обеспечить инкапсуляцию данных, скрывая их реализацию и предоставляя контролируемый доступ к ним
* валидация данных: возможность добавления логики проверки данных на соответствие определенным правилам или условиям в методах, реализующих паттерн Свойство
* ленивая инициализация: паттерн Свойство может быть использован для реализации ленивой инициализации, при которой инициализация объекта или вычисление значения откладывается до момента его фактического использования

{% hint style="info" %}
Основная цель ленивой инициализации - избежать необязательных ресурсозатратных операций или вычислений, которые могут быть не нужны до момента использования объекта. Это позволяет повысить производительность и эффективность написанной программы.
{% endhint %}

## Преимущества

* реализация принципа инкапсуляции
* обеспечение контроля доступа к данным, которое позволяет избежать ошибок при работе с объектами
* возможность добавлять дополнительную логику при доступе к данным (например, проверку на корректность значений или логирования запроса доступа к данным)

## Недостатки

* приводит к увеличению количества типового кода, так как для каждого поля объекта требуется создание методов доступа

## Связь с другими паттернами

* [Одиночка](../../creationals-patterns/singleton/): паттерн Свойство может быть частью реализации паттерна Одиночки. В этом случае свойство, представляющее экземпляр Singleton класса, может быть доступно через геттер и сеттер методы Property.
* [Декоратор](../../structural-patterns/dekorator/): паттерн Свойство может использоваться вместе с паттерном Декоратор для добавления дополнительной функциональности к свойству объекта. Декоратор может обернуть объект Свойства и расширить его поведение без изменения самого объекта.
* [Заместитель](../../structural-patterns/proxy/): паттерн Свойство может быть реализован в виде прокси-объекта, который обеспечивает контроль доступа к свойству. Заместитель может добавлять дополнительную логику перед доступом к свойству или ограничивать доступ к нему.
* [Адаптер](../../structural-patterns/adapter/): паттерн Свойство может быть использован в связке с паттерном Adapter для адаптации интерфейса свойства к требуемому интерфейсу.
