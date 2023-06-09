Чтобы спуллить образ из github registry:

```docker pull ghcr.io/catnyan02/task_safe_board:1.0.0```

Чтобы запустить его:

```docker run -p 8000:8000 ghcr.io/catnyan02/task_safe_board:1.0.0```

Веб-интерфейс запустится по адресу: http://127.0.0.1:8000

Протестировать его работу можно при помощи Swagger документации: http://127.0.0.1:8000/api/docs

В качестве процесса я решила взять запуск SPASS (автоматизированного
средства доказательства теорем логики первого порядка) 
Я нашла пример задачки, которую SPASS решает долго, 
поэтому процесс удовлетворяет обоим условиям.

Я слегка изменила endpoints, теперь start осуществляется при помощи метода
POST, stop при помощи DELETE, без параметров, так как это больше отвечает
Best Practices для REST API. А так же добавила в них исключения 400,
если пытаемся запустить уже запущенный процесс и если пытаемся удалить
незапущенный процесс.

В статус процесса я добавила дополнительные метрики. Сколько времени процесс запущен, 
сколько процентов CPU и памяти он потребляет.
