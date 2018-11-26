# SETUP.JSON в темах InSales

## Назначение файла

Данный файл описывает, что нужно создавать в магазине при установке или инициализации темы.

---

## Перечень объектов доступных для создания

### Категории на сайте

Массив категорий. Задается идентификатор и название каждой категории.

Структура:

```JSON
"collections": {
  "apparel":"Одежда",
  "Tehnika":"Модная одежда",
}
```

### Шаблон панели блоков

Шаблоны блоков записываются в поле `block_templates` которое является объектом.

У шаблонов есть 2 обязательных поля - `name`, `block_fields`.

**name** - имя блока

**block_fields** - поля блока

У полей блоков могут быть поля `name`, `kind`, `block_field_options`.

**name** - имя поля

**kind** - тип поля

**block_field_options** - список опций селекта

Типы полей:

- `text` - Текст

- `rich_text` - HTML

- `account_file` - Файл

- `collection_list` - Список категорий

- `collection` - Категория

- `select` - Выпадающий список

- `checkbox` - Чекбокс

Структура:

```JSON
{
  "block_templates": {
    "slider-block": {
      "name": "Слайдер",
      "block_fields": {
        "link": {
          "name": "Ссылка",
          "kind": "text"
        },
        "description": {
          "name": "Контент",
          "kind": "rich_text"
        },
        "heading": {
          "name": "Заголовок",
          "kind": "text"
        },
        "collection": {
          "name": "Категория",
          "kind": "collection"
        },
        "image": {
          "name": "Изображения",
          "kind": "account_file"
        },
        "hide_heading": {
          "name": "Скрыть заголовок?",
          "kind": "checkbox"
        },
        "side": {
          "kind" : "select",
          "name" : "Расположение изображения",
          "block_field_options": {
            "is-right": "Справа",
            "is-left": "Слева"
          }
        }
      }
    }
  }
}
```

### Панели блоков

Задается идентификатор и название каждой панели блоков. Можно также задать идентификаторы блоков, которые надо добавить на панель.

Структура:

```JSON
"block_lists": {
  "left": {
    "title": "Блоки в категориях слева",
    "blocks": ["special-offer", "banner"]
  }
}
```

### Панель блоков с привязанным шаблоном

Структура:

```JSON
"block_lists": {
  "left": {
    "title": "Блоки в категориях слева",
    "blocks": ["special-offer", "banner"],
    "block_template": "system-title-and-content"
  }
}
```

### Блоки
Задается идентификатор, название и содержимое блока.

Структура:

```JSON
"blocks": {
  "banner": {
    "title": "Акции и распродажи",
    "content": "50% на все товары!"
  }
}
```

### Блок с привязанным шаблоном

Структура:

```JSON
"blocks": {
  "banner": {
    "title": "Акции и распродажи",
    "content": "50% на все товары!",
    "block_template": "system-title-and-content"
  }
}
```

### Блок с кастомным шаблоном

Структура:

```JSON
"blocks": {
  "first-slider": {
    "title": "Акции и распродажи",
    "heading": "Акции и распродажи",
    "description": "50% на все товары!",
    "link": "/page/sale",
    "block_template": "slider-block"
  }
},
"block_lists": {
  "index-slider": {
    "title": "Слайдер",
    "blocks": ["first-slider"],
    "block_template": "slider-block"
  }
},
"block_templates": {
  "slider-block": {
    "name": "Слайдер",
    "block_fields": {
      "link": {
        "name": "Ссылка",
        "kind": "text"
      },
      "description": {
        "name": "Контент",
        "kind": "rich_text"
      },
      "heading": {
        "name": "Заголовок",
        "kind": "text"
      },
      "collection": {
        "name": "Категория",
        "kind": "collection"
      },
      "image": {
        "name": "Изображения",
        "kind": "account_file"
      }
    }
  }
}
```

### Блоги
Задается идентификатор и название каждого. Также можно для блога задать список статей.

Структура:

```JSON
"blogs": {
  "news": "Новинки",
  "sales": {
    "title": "Скидки",
    "articles": {
      "winter": "20% на зимнюю коллекцию",
      "shose": {
        "title": "5% на всю обувь",
        "content": "5% на всю обувь",
        "preview": "Обувь со скидкой!",
        "author": "Админимтрация"
      }
    }
  }
}
```

### Страницы
Для страницы можно задать название, идентификатор и содержание.

```json
"pages": {
  "delivery": "Доставка",
  "payment": "Оплата" ,
  "privacy-policy": {
    "title": "Политика безопасности",
    "content": "У нас все секьюрно)"
  }
}
```

### Параметры и их значения
Задаются идентификаторы, названия и списки значений параметров.

Структура:

```JSON
"properties": {
  "property_permalink": {
    "title": "my_property",
    "characteristics": {
      "char_permalink_1": "char_title_1", "char_permalink_2": "char_title_2"
    }
  }
}
```

### Меню
Массив меню. Задается идентификатор и название каждого меню. Массив пунктов меню. Задается идентификатор и название каждого пункта меню и указывается в какое меню добавлять.

Структура:

```JSON
"menus": {
  "main-menu":"Верхнее меню",
  "first-footer":"Нижнее меню"
},
"menu_items": {
  "main-menu": { "Ссылка1": "http://ya.ru", "Ссылка2": "cart", "Ссылка3": "account" }
}
```


## Пример файла

```JSON
{
  "collections": {
    "apparel":"Одежда",
    "Tehnika":"Модная одежда",
    "Aksessuary":"Джинсы",
    "featured_products":"Рекомендуемые товары",
    "new":"Новые товары",
    "popular":"популярные товары"
  },
  "block_lists": {
    "left":"Блоки в категориях слева"
  },
  "blocks": {
    "Банер":"Акции и распродажи",
    "Tovar-nedeli":"Товар недели",
    "условия-доставки":"Условия доставки"
  },
  "blogs": {
    "my_blog1": "мой блог1",
    "my_blog2": "мой блог2"
  },
  "properties": {
    "property_permalink": {
      "title": "my_property",
      "characteristics": { "char_permalink_1": "char_title_1", "char_permalink_2": "char_title_2" }
    }
  },
  "menus": {
    "main-menu":"Верхнее меню",
    "first-footer":"Нижнее меню",
    "second-footer":"Второе меню"
  },
  "menu_items": {
    "main-menu": {
      "Ссылка1": "http://ya.ru",
      "Ссылка2": "cart",
      "Ссылка3": "account"
    }
  }
}
```
