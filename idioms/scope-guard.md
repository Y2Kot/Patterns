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

# Scope guard

## Назначение

Идиома Scope-guard (область-хранитель) является подходом в программировании, который используется для автоматического освобождения ресурсов и выполнения определенных действий при выходе из области видимости (scope) в программе. Используется при:

1. Работе с ресурсами, которые должны быть освобождены в случае исключения.
2. Реализации обратных вызовов (например, при регистрации обработчика событий в библиотеке или фреймворке, Scope Guard может быть использован для отмены регистрации обработчика, когда он больше не нужен.).
3. Работе с транзакциями (например, при работе с базами данных, транзакции могут быть начаты в конструкторе объекта и завершены в деструкторе. Scope Guard может быть использован для отката транзакции, если произошло исключение, но не для освобождения ресурсов, связанных с транзакцией.)

## Решаемые задачи

* Сохранение ресурсов при выходе из области видимости, если исключение не проброшено

Идиома [RAII](raii.md) позволяет получать ресурсы в конструкторе и высвобождать их в деструкторе, когда область заканчивается успешно или из-за исключения. Однако, иногда необходимо не высвобождать ресурсы, если исключение не выбрасывается. Идиома Scope-guard решить эту задачу и улучшить типичную реализацию идиомы RAII с помощью условной проверки.

## Общая реализация на языке C++

{% tabs %}
{% tab title="ScopeGuard" %}
{% code fullWidth="true" %}
```cpp
class ScopeGuard {
public:
    ScopeGuard () : engaged_(true) 
    { 
        /* Выделение ресурсов */ 
    }
  
    ~ScopeGuard() {
        if (engaged_) 
        { 
            /* Освобождение ресурсов */ 
        }
    }

    void release()
    {
        engaged_ = false;
        /* Ресурсы больше не будут освобождаться */
    }
private:
    bool engaged_;
};
```
{% endcode %}
{% endtab %}
{% endtabs %}

<pre class="language-cpp" data-full-width="true"><code class="lang-cpp"><strong>void some_init_function()
</strong>{
    ScopeGuard guard;
    // если выброситься какая-то ошибка, ресурсы будут освобождены.
    guard.release(); // Ресурсы не будут освобождены при обычном выполнении.
}
</code></pre>
