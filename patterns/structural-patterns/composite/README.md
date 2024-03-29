---
description: Composite
---

# Компоновщик

## Назначение

Компоновщик (Composite) - структурный паттерн проектирования, который позволяет сгруппировать объекты в древовидные структуры для представления иерархий "часть-целое". Позволяет клиентам единообразно трактовать индивидуальные и составные объекты.

#### Используется в случаях, когда:

* Необходимо объединять группы схожих объектов и управлять ими.
* Объекты могут быть как примитивными (элементарными), так и составными (сложными). Составной объект может включать в себя коллекции других объектов, образуя сложные древовидные структуры.

{% hint style="info" %}
Пример: директория файловой системы состоит из элементов, каждый их которых также может быть директорией.
{% endhint %}

* Код клиента работает с примитивными и составными объектами единообразно.

## Решаемые задачи

* композиция объектов

Дает возможность представления иерархии объектов вида часть-целое. С помощью композиции можно создавать древовидные структуры объектов, группировать объекты в контейнеры и управлять ими единообразно.

* предоставление единообразного интерфейса

Единообразная трактовка клиентами составных и индивидуальных объектов, то есть паттерн компоновщик позволяет клиентам взаимодействовать с отдельными объектами и группами объектов (составными объектами) через единый интерфейс.

{% hint style="info" %}
В качестве клиентов может выступать пользовательский код или другие классы, взаимодействующие с объектами иерархии Composite.
{% endhint %}

* создание рекурсивных операций

Паттерн компоновщик позволяет выполнять операции на составных объектах рекурсивно. Когда операция вызывается на составном объекте, он автоматически распространяет операцию на все объекты в иерархии, включая объекты, содержащие другие объекты. Происходит рекурсивный проход по иерархии. Таким образом, можно легко применять операции как к отдельным объектам, так и ко всему дереву объектов.

## UML диаграмма

<div data-full-width="true">

<figure><img src="../../../.gitbook/assets/composite_white (1).png" alt=""><figcaption><p>UML диаграмма паттерна "Компоновщик"</p></figcaption></figure>

</div>

## Преимущества

* упрощение архитектуры клиентского кода

Предоставление клиентскому коду удобного и единого интерфейса для работы как с отдельными, так и с составными объектами позволяет ему работать с иерархией объектов без необходимости проверять их типы и выбирать разные пути обработки.

* повышение гибкости и расширяемости системы за счет добавления новых компонентов в иерархию без изменения существующего кода
* возможность выполнения рекурсивных операций на составных объектах
* предоставление удобных методов для добавления, удаления и обхода компонентов в иерархии объектов

## Недостатки

* потребность в создании сущности, отвечающей за за логику сборки компоновщика, которая может оказаться нетривиальной
* нетривиальная логика обхода и работы с сущностью как с контейнером, если в компоновщике содержатся другие компоновщики
* потеря типизации

Использование общего интерфейса может привести к потере типизации и нарушению статической проверки типов. Появляется необходимость решать проблему типизации вынесением всех методов из компоновщика в класс компонента. В свою очередь, это приводит к следующей проблеме

* появление нелогичных операций

Максимизация интерфейса класса компонент, приводит к тому, что у подклассов появляются нелогичные операции

## Связь с другими паттернами

* [Цепочка обязанностей](../../behavioral-patterns/chain-of-responsibility/): отношение компонент-родитель используется в паттерне цепочка обязанностей.
* [Декоратор](../dekorator/): паттерн декоратор часто применяется совместно с компоновщиком. Когда декораторы и компоновщики используются вместе, у них обычно бывает общий родительский класс. Поэтому декораторам придется поддержать интерфейс компонента такими операциями, как Add, Remove.
* [Приспособленец](../prisposoblenec/): паттерн приспособленец позволяет разделять компоненты, но ссылаться на своих родителей они уже не могут.
* [Итератор](../../behavioral-patterns/iterator/): итератор можно использовать для обхода составных объектов.
* [Посетитель](../../behavioral-patterns/visitor/): посетитель локализует операции и поведение, которые в противном случае пришлось бы распределять между классами Composite и Leaf

{% hint style="info" %}
**Leaf** – лист:

– представляет листовые узлы композиции и не имеет потомков;

– определяет поведение примитивных объектов в композиции;

**Composite** – составной объект:

– определяет поведение компонентов, у которых есть потомки;

– хранит компоненты-потомки;

– реализует относящиеся к управлению потомками операции в интерфейсе класса Component;

**Component** – компонент:

– объявляет интерфейс для компонуемых объектов;

– предоставляет подходящую реализацию операций по умолчанию, общую для всех классов;

– объявляет интерфейс для доступа к потомкам и управления ими;
{% endhint %}
