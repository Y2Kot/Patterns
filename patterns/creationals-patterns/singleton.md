---
description: Singleton
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Одиночка

## Назначение

Одиночка (Singleton) – это порождающий паттерн проектирования, который гарантирует, что у класса есть только один экземпляр, и предоставляет к нему глобальную точку доступа. Этот экземпляр создается внутри класса и предоставляется через статический метод. Используется когда требуется глобальный доступ к экземпляру объекта или контроль над созданием и инициализацией из любой части программы.

{% hint style="info" %}
Примером такого объекта может являться объект базы данных. Такие объекты нельзя клонировать или копировать, объект должен быть один во всей системе. Это необходимо для того, чтобы избежать проблем с целостностью и согласованностью данных.
{% endhint %}

## Решаемые задачи

* Контроть за объектом.

Паттерн гарантирует, что у класса есть только один экземпляр, что необходимо, когда требуется контролировать количество созданных объектов и предотвращать их дублирование из любой части программы.

* Оптимизация использования ресурсов.

Появляется возможность оптимизировать использование ресурсов, что важно, когда создание объекта требует значительных ресурсов.

## Общая реализация на языке C++

{% tabs %}
{% tab title="Product" %}
{% hint style="info" %}
Конструктор помечается модификатором private, чтобы объект класса нельзя было создать извне
{% endhint %}

{% code fullWidth="true" %}
```cpp
class Product
{
public:
   static shared_ptr<Product> instance()
   {
       static shared_ptr<Product> myInstance(new Product());
       return myInstance;
   }
   
   ~Product() 
   {
        cout << "Destructor;" << endl; 
   }

   void f() 
   {
        cout << "Method f;" << endl; 
   }

   Product(const Product&) = delete; 
   Product& operator=(const Product&) = delete; 

private:
   Product() 
   { 
        cout << "Default constructor;" << endl; 
   }
};
```
{% endcode %}
{% endtab %}
{% endtabs %}

```cpp
# include <iostream>
# include <memory>

using namespace std;

int main()
{
   shared_ptr<Product> ptr(Product::instance());

   ptr->f();
}
```

## Преимущества

1. Гарантия наличия единственного экземпляра объекта.
2. Предоставление глобальной точки доступа к объекту.

## Недостатки

1. Одиночку называют "Анти-паттерн" из-за глобального доступа, так как это создает проблемы с модификацией, расширением и управлением объектом.
2. Нарушается прицип единой ответственности. Объект помимо своей основной функциональности, также отвечает за управление своим глобальным состоянием и доступом из других частей программы.
3. Решение о том, какой объект создавать не может приниматься при выполнении программы.
4. Усложняется написание модульных тестов.

## Связь с другими паттернами

1. Паттерн [Абстрактная фабрика](abstract-factory.md) может использовать Одиночку для хранения экземпляра фабрики и предоставления глобального доступа к ней. Это может быть полезно, если требуется создавать различные объекты с помощью фабрики, но необходимо гарантировать единственность экземпляра.
2. При использовании паттерна [Прототип](prototype.md) для создания новых объектов посредством клонирования существующих, одиночка может быть использован для хранения прототипов и предоставления глобального доступа к ним. Таким образом, объект Одиночка может служить реестром прототипов, упрощая создание новых объектов на основе существующих.
3. Паттерн [Фасад](../structural-patterns/facade.md) может использовать Одиночку для предоставления глобального доступа к объекту, который предоставляет простой интерфейс для взаимодействия с комплексной подсистемой.
