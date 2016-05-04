---
title: scheduler.md
layout: post
source-id: 1J_cDTx-uXTR2EkM79l1CnkKXb_hCMgy0j-YgheYQTzc
published: true
---
### 6.2 Налаштування Планувальника Scheduler

Планувальник Scheduler це компонент WebMagic для управління списком черги URL-ів. Загалом планувальник виконує 2 функції:

1. Управління списком черги URL-ів, що чекають на обробки пошукачем

2. Відфільтровувати повтори URL-ів

WebMagic мають деякі загальні Scheduler. Якщо ви хочете запустити простий пошукач, то вам не потрібно налаштувати Планувальник Scheduler. Але має сенс для вас знати деякі з функцій.

|Class|Опис|Зауваження|

З версії 0.5.1 перероблено планувальник Scheduler: видалення дублів було винесено до окремого інтерфейсу: `DuplicateRemover`. Завдяки цьому ви можете встановити різні `DuplicateRemover` для одного планувальника Scheduler. Є два способи видалити дублікати.

|Class|Опис|

Всі планувальники за замовчуванням для видалення використовують `HashSetDuplicateRemover` (окрім `RedisScheduler`). Якщо у вас дуже багато URL, рекомендуємо використовувати `BloomFilterDuplicateRemover`. Наприклад:

```java

spider.setScheduler(new QueueScheduler()

```
