# cert_generator
Генераторов сертификатов участия в конференции.

## Содержание

- [cert_generator](#cert_generator)
  - [Содержание](#содержание)
  - [1. Принцип работы генератора](#1-принцип-работы-генератора)
    - [1.1 Запуск генератора](#11-запуск-генератора)
    - [1.2 Описание работы генератора](#12-описание-работы-генератора)

## 1. Принцип работы генератора

### 1.1 Запуск генератора

Команда запуска:
- Для Linux: `python3 gen_partics.py sample_name authors_list`
- Для Windows: `py gen_partics.py sample_name authors_list`

Необходимые файлы для работы, передаваемые в виде параметров:

| Название файла | Описание                                                                                 |
| -------------- | ---------------------------------------------------------------------------------------- |
| `sample_name`  | Путь до файла шаблона, в котором будет заменятся информация. Должен иметь формат `.fodt` |
| `authors_list` | Путь до файла списка участников. Должен иметь формат `.csv`                              |

Для получения справки можно воспользоваться командой:
- Для Linux: `python3 gen_partics.py -h`
- Для Windows: `py gen_partics.py -h`

### 1.2 Описание работы генератора

Генератор ищет шаблон, указанный как параметр `sample_name` в папке. После замены на данные из файла, указанного, как параметр `authors_list`,
генератор формирует файлы `.fodg` в папку `./cert/<имя_шаблона_из_параметра_sample_name>`. Имена выходных фалов будут совпадать с ФИО участника, для которого они сделаны.

Генератор заменяет данные по следующему принципу:

| Название поля | Имя соответствующей переменной в шаблоне | Описание                                |
| ------------- | :--------------------------------------: | --------------------------------------- |
| `gender`      |               `AUTHORFIO`                | Гендер участника *(выступил\выступила)* |
| `fio`         |              `AUTHORGENDER`              | ФИО участника                           |
| `doc`         |               `AUTHORDOC`                | Название доклада участника              |

Данные для подстановки из файла `.csv`, указанного, как параметр `sample_name`, в шаблон имеют вид, как на данном примере:
```
gender;fio;doc
выступил;Перескоков Александр Вадимович;Об асимптотике спектра оператора типа Хартри с экранированным кулоновским потенциалом самодействия вблизи верхних границ спектральных кластеров
выступила;Фоменко Татьяна Николаевна;Нули функционалов и параметрическая теорема Майкла о сечениях
```