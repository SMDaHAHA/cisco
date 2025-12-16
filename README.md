### Перезагрузка cisco CLI

> [!cicso]
> CISCO#reload in 1
> Перезагрузка циски через 1 минуту, сбросятся настройки

## Вход в режим конфигурации

> [!cicso]
> CISCO#conf t
> Вход в режим конфигурации

# ?
> **Помогает в понимание синтаксиса и изучение аргументов, используется без пробела**
> man????

# Все уровни cisco и быстрые команды

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251216234257.png))

| Команда        | Описание                                                        |
| -------------- | --------------------------------------------------------------- |
| Ctrl+A         | Перемещение курсора в начало строки                             |
| Ctrl+E         | Перемещение курсора в конец строки                              |
| Esc+B          | Перемещение курсора на одно слово назад                         |
| Ctrl+F         | Перемещение курсора вперед на один символ                       |
| Esc+F          | Перемещение вперед на одно слово                                |
| Ctrl+D         | Удаление одного символа                                         |
| Ctrl+R         | Повторный вывод строки                                          |
| Ctrl+U         | Стирание строки                                                 |
| Ctrl+W         | Стирание слова                                                  |
| ==**Ctrl+Z**== | ==**Завершение режима конфигурирования и возврашение в EXEC**== |
| ==*Tab*==      | ==*Завершение ввода команды маршрутизатором*==                  |

# Журнал использования

| Команда                                   | Описание                                                         |
| ----------------------------------------- | ---------------------------------------------------------------- |
| Ctrl+P или стрелка вверх                  | Показывает последнюю введенную команду                           |
| Ctrl+N или стрелка вниз                   | Демонстрирует предыдущую введенную команду                       |
| show history                              | По умолчанию показывает 10 последних введенных команд            |
| show terminal                             | Показывает конфигурацию терминала и размер буфера журнала команд |
| Terminal history size "`число макс. 256`" | Изменяет размер буфера (максимум 256)                            |

### Просмотр всех интерфейсов

```
CISCO#show interfaces status
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212095541.png)

статус всех подключений

```
CISCO#show interfaces status | in connected
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212102854.png)

# Конфиги

```
CISCO#show startup-config
```

Показывает содержимое конфигурации, которая применяется при загрузке. Можно скопировать эти данные в буфер обмена и сохранить в файл в качестве бэкапа конфигурации. Этот файл потом можно просто вставить (с небольшими оговорками) из буфера обмена в экран консоли, дать команду wr mem, и этим восстановить конфигурацию (многие программы, автоматически сохраняющие и обновляющие конфигурацию, применяют как раз такой метод).  
  
```
CISCO#show running-config
```

Команда show running-config показывает текущую конфигурацию устройства. Running-configuration – это конфигурация, загруженная в данный момент в оперативную память роутера. Когда вы вносите изменения в оборудование, как раз эта конфигурация изменяется. НО ПОСЛЕ ПЕРЕЗАГРУЗКИ ОН ЗАМЕНЯЕТСЯ НА startup-config, так что не бойтесь испортить после перезагрузки все вернеться.  
  
```
CISCO#copy startup-config running-config
```

Отменяет все сделанные (если были) изменения в конфигурации. То же самое произойдет, если выключить/включить питание (перезагрузить устройство).

```
CISCO#running-config startup-config 
```

Сохраняет в энергонезависимой памяти все изменения, сделанные в конфигурации. Полный аналог команды write или write memory.

#### Загрузка конфигурации

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212104958.png)

```
CISCO#copy running-config startup-config
```


```
CISCO#wr
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212114040.png)

### Просмотр порт группы

```
CISCO#show etherchannel summary
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212095848.png)
посмотреть группу каналов


```
CISCO#show run interface po2
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212100058.png)
показывает информацию об интерфейсе *порт-группы*
### Посмотреть информацию о интерфейсе 

```
CISCO#show interface po2
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212100225.png)

```
CISCO#show run interface 1/0/47
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212103729.png)
Выведет информацию из текущей конфигурации

# Соседние cisco (ВАЖНО)

```
CISCO#show cdp neighbors
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212100649.png)
Показывает соседние cisco устройство, всю нужную информацию, сверху ==ЛЕГЕНДА==

```
CISCO#show version
```

показывает текущую версию

### для перенаправления логов cisco

```
CISCO#do terminal mon
```
В режиме конфигурации (conf t)
![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212101933.png)


## Освобождение, убираем порты из порт группы
(conf t)
```
CISCO(config)#interface gigabitEthernet 0/24
```
выбираем интерфейс
```
CISCO(config-if)#shutdown
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212102015.png)

Выбираем интерфейс
и офаем его (down - отключение, опускаем xD)
![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212102444.png)
т.к. Terminal mon включен
выводятся логи (узнать инфу по логам)

```
CISCO(config-if)#do show interface gi0/24
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212102344.png)

### Описание интерфейса

```
CISCO(config-if)#description TO_SW001G
```
(описание интерфейса)


### Копирование в начальную конфигурацию

```
CISCO#copy running-config startup-config
```

![Image alt](https://github.com/SMDaHAHA/cisco/blob/main/png/Pasted%20image%2020251212114204.png)
