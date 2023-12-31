# Stream
## Бесконечные последовательности

    //Генерация бесконевчного потока данных
    Scanner scanner = new Scanner(System.in);
    Stream<String> s = Stream.generate(() -> scanner.nexLine());
    //чтобы фильтровать значеня есть
    s.filter()//в аргументах можно узать критерий, по которому будет отфильтровываться информация

В потоках есть методы конвейерные и терминальные

### Конвейерные методы

| Метод stream                                          | Описание                                                                           | Пример                                                                                                           |
|-------------------------------------------------------|------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| filter                                                | Отфильтровывает записи, возвращает только записи, соответствующие условию          | collection.stream().filter(«a1»::equals).count()                                                                 |
| skip                                                  | Позволяет пропустить N первых элементов                                            | collection.stream().skip(collection.size() — 1).findFirst().orElse(«1»)                                          |
| distinct                                              | Возвращает стрим без дубликатов (для метода equals)                                | collection.stream().distinct().collect(Collectors.toList())                                                      |
| map                                                   | Преобразует каждый элемент стрима                                                  | collection.stream().map((s) -> s + "_1").collect(Collectors.toList())                                            |
| peek                                                  | Возвращает тот же стрим, но применяет функцию к каждому элементу стрима            | collection.stream().map(String::toUpperCase).peek((e) -> System.out.print("," + e)).collect(Collectors.toList()) |
| limit                                                 | Позволяет ограничить выборку определенным количеством первых элементов             | collection.stream().limit(2).collect(Collectors.toList())                                                        |
| sorted                                                | Позволяет сортировать значения либо в натуральном порядке, либо задавая Comparator | collection.stream().sorted().collect(Collectors.toList())                                                        |
| mapToInt, mapToDouble, mapToLong                      | Аналог map, но возвращает числовой стрим (то есть стрим из числовых примитивов)    | collection.stream().mapToInt((s) -> Integer.parseInt(s)).toArray()                                               |
| flatMap, flatMapToInt, flatMapToDouble, flatMapToLong | Похоже на map, но может создавать из одного элемента несколько                     | collection.stream().flatMap((p) -> Arrays.asList(p.split(",")).stream()).toArray(String[]::new)                  |



### Терминальные методы

| Метод stream   | Описание                                                                                         | Пример                                                                          |
|----------------|--------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| findFirst      | Возвращает первый элемент из стрима (возвращает Optional)                                        | collection.stream().findFirst().orElse(«1»)                                     |
| findAny        | Возвращает любой подходящий элемент из стрима (возвращает Optional)                              | collection.stream().findAny().orElse(«1»)                                       |
| collect        | Представление результатов в виде коллекций и других структур данных                              | collection.stream().filter((s) -> s.contains(«1»)).collect(Collectors.toList()) |
| count          | Возвращает количество элементов в стриме                                                         | collection.stream().filter(«a1»::equals).count()                                |
| anyMatch       | Возвращает true, если условие выполняется хотя бы для одного элемента                            | collection.stream().anyMatch(«a1»::equals)                                      |
| noneMatch      | Возвращает true, если условие не выполняется ни для одного элемента                              | collection.stream().noneMatch(«a8»::equals)                                     |
| allMatch       | Возвращает true, если условие выполняется для всех элементов                                     | collection.stream().allMatch((s) -> s.contains(«1»))                            |
| min            | Возвращает минимальный элемент, в качестве условия использует компаратор                         | collection.stream().min(String::compareTo).get()                                |
| max            | Возвращает максимальный элемент, в качестве условия использует компаратор                        | collection.stream().max(String::compareTo).get()                                |
| forEach        | Применяет функцию к каждому объекту стрима, порядок при параллельном выполнении не гарантируется | set.stream().forEach((p) -> p.append("_1"));                                    |
| forEachOrdered | Применяет функцию к каждому объекту стрима, сохранение порядка элементов гарантирует             | list.stream().forEachOrdered((p) -> p.append("_new"));                          |
| toArray        | Возвращает массив значений стрима                                                                | collection.stream().map(String::toUpperCase).toArray(String[]::new);            |
| reduce         | Позволяет выполнять агрегатные функции на всей коллекцией и возвращать один результат            | collection.stream().reduce((s1, s2) -> s1 + s2).orElse(0)                       |


### Дополнительные методы для числовых потоков

| Метод stream | Описание                                       | Пример                                                             |
|--------------|------------------------------------------------|--------------------------------------------------------------------|
| sum          | Возвращает сумму всех чисел                    | collection.stream().mapToInt((s) -> Integer.parseInt(s)).sum()     |
| average      | Возвращает среднее арифметическое всех чисел   | collection.stream().mapToInt((s) -> Integer.parseInt(s)).average() |
| mapToObj     | Преобразует числовой стрим обратно в объектный | intStream.mapToObj((id) -> new Key(id)).toArray()                  |

### Ещё несколько методов

| Метод stream | Описание                                                                                      |
|--------------|-----------------------------------------------------------------------------------------------|
| isParallel   | Узнать является ли стрим параллельным                                                         |
| parallel     | Вернуть параллельный стрим, если стрим уже параллельный, то может вернуть самого себя         |
| sequential   | Вернуть последовательный стрим, если стрим уже последовательный, то может вернуть самого себя |



### [источник](https://webhamster.ru/mytetrashare/index/mtb426/1578962094eafr3wruxs)