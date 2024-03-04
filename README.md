1_4

Первый контакт
Описание
Контакты — удобное приложение. Он хранит все ваши сохраненные контакты. В этом проекте вы напишете его сами. Он учит вас понимать и реализовывать основные принципы ООП.

На первом этапе следует написать программу, создающую экземпляр класса, хранящего информацию об одной записи в Контактах. Одна запись должна содержать имя, фамилию и номер телефона. Вы можете набирать их с клавиатуры.

Вам также следует создать класс, представляющий это приложение. На данный момент он должен хранить только одну запись: запись, которую вы создали на основе входных данных.

Пример
Ниже приведен пример того, как может выглядеть ваш результат. Строки, начинающиеся с, > представляют вводимые пользователем данные.

Enter the name of the person:
> John
Enter the surname of the person:
> Smith
Enter the number:
> 1-234-567-890

A record created!
A Phone Book with a single record created!

2_4

Создать меню
Описание
Иногда нам необходимо ограничить возможность изменения свойств экземпляра. Например, номер телефона не может быть простой строкой; оно должно следовать некоторым правилам. Как вы можете видеть здесь , формат номера телефона различен для каждой страны, но все они имеют некоторые общие элементы.

Итак, вам следует сделать свойство с номером телефона частным и создать метод получения и установки для этого свойства. Установщик должен проверить значение с помощью регулярного выражения и установить значение свойства только в том случае, если значение удовлетворяет всем приведенным ниже правилам:

Номер телефона следует разделить на группы с помощью пробела или тире. Возможна и одна группа.
Перед первой группой может быть или не быть знак плюса.
Первую или вторую группу можно заключить в круглые скобки, но в скобках не должно быть более одной группы. Также может отсутствовать группа, заключенная в круглые скобки.
Группа может содержать цифры, прописные и строчные английские буквы. Длина группы должна быть не менее 2 символов. Но первая группа может иметь длину всего один символ.
Если у вас возникли проблемы с регулярным выражением, которое проверяет все это, вы можете проверить номер телефона только с помощью строковых методов.
Также создайте геттеры и сеттеры для имени и фамилии человека. Кроме того, должен быть метод hasNumber(), проверяющий, есть ли у пользователя номер. Первоначально установите число как пустую строку.

Создайте отдельный метод для проверки достоверности номера телефона. Это автономная логика, и потенциально ее можно использовать в нескольких местах класса. Но это также метод для внутреннего применения. Поэтому отметьте метод как частный.

Эта концепция ограничения использования класса называется инкапсуляцией . Это самодокументированное решение о том, как использовать класс.

На этом этапе вам следует написать программу, которая хранит все записи в списке. У вас должна быть возможность добавлять, удалять, редактировать записи и получать количество записей. Если пользователь вводит неправильный номер телефона, вам следует сбросить его как пустой. [no number]Если число пустое, вместо него следует написать строку .

Примеры
Ниже приведен пример того, как может выглядеть ваш результат. Символ >представляет ввод пользователя.

Пример 1:

Enter action (add, remove, edit, count, list, exit): > count
The Phone Book has 0 records.
Enter action (add, remove, edit, count, list, exit): > edit
No records to edit!
Enter action (add, remove, edit, count, list, exit): > remove
No records to remove!
Enter action (add, remove, edit, count, list, exit): > add
Enter the name: > John
Enter the surname: > Smith
Enter the number: > +0 (123) 456-789-ABcd
The record added.
Enter action (add, remove, edit, count, list, exit): > add
Enter the name: > Adam
Enter the surname: > Jones
Enter the number: > +0(123)456-789-9999
Wrong number format!
The record added.
Enter action (add, remove, edit, count, list, exit): > list
1. John Smith, +0 (123) 456-789-ABcd
2. Adam Jones, [no number]
Enter action (add, remove, edit, count, list, exit): > edit
1. John Smith, +0 (123) 456-789-ABcd
2. Adam Jones, [no number]
Select a record: > 2
Select a field (name, surname, number): > number
Enter number: > (123) 234 345-456
The record updated!
Enter action (add, remove, edit, count, list, exit): > list
1. John Smith, +0 (123) 456-789-ABcd
2. Adam Jones, (123) 234 345-456
Enter action (add, remove, edit, count, list, exit): > remove
1. John Smith, +0 (123) 456-789-ABcd
2. Adam Jones, (123) 234 345-456
Select a record: > 1
The record removed!
Enter action (add, remove, edit, count, list, exit): > list
1. Adam Jones, (123) 234 345-456
Enter action (add, remove, edit, count, list, exit): > exit
Пример 2:

Enter action (add, remove, edit, count, list, exit): > add
Enter the name: > John
Enter the surname: > Smith
Enter the number: > +0 (123) 456-789-ABcd
The record added.
Enter action (add, remove, edit, count, list, exit): > edit
1. John Smith, +0 (123) 456-789-ABcd
Select a record: > 1
Select a field (name, surname, number): > number
Enter number: > ()()
Wrong number format!
The record updated!
Enter action (add, remove, edit, count, list, exit): > list
1. John Smith, [no number]
Enter action (add, remove, edit, count, list, exit): > exit

3_4

Обновите свои контакты
Описание
На этом этапе вы напишете программу, которая сможет хранить информацию не только о людях, но и об организациях.

В реальном приложении вы также можете хранить номера телефонов разных компаний, например вашего любимого магазина пиццы или банка. У этих организаций нет ни имени, ни фамилии; у них есть название организации и адрес.

Кроме того, у человека может быть дата рождения и пол, но у компании этого быть не может.

Давайте воспользуемся наследованием , чтобы решить эту проблему. Должен быть базовый класс, содержащий информацию, относящуюся как к организации, так и к человеку, например номер телефона. И должно быть два класса, наследующих этот базовый класс: класс, представляющий организацию, и класс, представляющий человека.

Список записей должен содержать как людей, так и организации. Этого можно добиться, если список записей содержит элементы базового класса, а не конкретных классов.

Здесь есть одна проблема: как можно редактировать свойства, соответствующие конкретным классам, например адрес организации? Одним из решений является создание последнего логического свойства isPersonв базовом классе. После этого при редактировании записи сначала проверьте это свойство, затем приведите к соответствующему классу и только потом редактируйте свойство. Это плохое обходное решение, но на следующем этапе мы напишем более общее решение.

Также на этом этапе вы можете улучшить базовый класс, чтобы у него было более одного свойства. Вам следует реализовать свойства, хранящие дату создания этой записи и дату последнего редактирования.

Используйте пустую строку для разделения различных действий, как в примере.
Пример
Ниже приведен пример того, как может выглядеть ваш результат. Символ > представляет ввод пользователя.

Enter action (add, remove, edit, count, info, exit): > add
Enter the type (person, organization): > person
Enter the name: > John
Enter the surname: > Smith
Enter the birth date: >
Bad birth date!
Enter the gender (M, F): >
Bad gender!
Enter the number: > +0 (123) 456-789-ABcd
The record added.

Enter action (add, remove, edit, count, info, exit): > add
Enter the type (person, organization): > organization
Enter the organization name: > Pizza Shop
Enter the address: > Wall St. 1
Enter the number: > +0 (123) 456-789-9999
The record added.

Enter action (add, remove, edit, count, info, exit): > info
1. John Smith
2. Pizza Shop
Enter index to show info: > 2
Organization name: Pizza shop
Address: Wall St. 1
Number: +0 (123) 456-789-9999
Time created: 2018-01-01T00:00
Time last edit: 2018-01-01T00:00

Enter action (add, remove, edit, count, info, exit): > edit
1. John Smith
2. Pizza Shop
Select a record: > 1
Select a field (name, surname, birth, gender, number): > number
Enter number: > (123) 234 345-456
The record updated!

Enter action (add, remove, edit, count, info, exit): > info
1. John Smith
2. Pizza Shop
Select a record: > 1
Name: John
Surname: Smith
Birth date: [no data]
Gender: [no data]
Number: (123) 234 345-456
Time created: 2018-01-01T00:00
Time last edit: 2018-01-01T00:01

Enter action (add, remove, edit, count, info, exit): > edit
1. John Smith
2. Pizza Shop
Select a record: > 2
Select a field (address, number): > address
Enter address: > Wall St. 7
The record updated!

Enter action (add, remove, edit, count, info, exit): > info
1. John Smith
2. Pizza Shop
Enter index to show info: > 2
Organization name: Pizza shop
Address: Wall St. 7
Number: +0 (123) 456-789-9999
Time created: 2018-01-01T00:00
Time last edit: 2018-01-01T00:02

Enter action (add, remove, edit, count, info, exit): > exit

4_4

Описание
Наше временное решение на предыдущем этапе было плохим, потому что каждый раз, когда вы хотите взаимодействовать с конкретными классами, вы должны проверить логическое свойство, а затем применить другой код в соответствии с конкретным классом. Пока все хорошо, вы реализуете это поведение каждый раз, когда вам это нужно. Однако в более крупном приложении может быть 100 и более мест, где вам необходимо это сделать. И, в конце концов, может поступить запрос на новую функцию: внедрить третий тип записей, который представляет собой автоматизированную систему с роботами, обслуживающими звонки. Вас бы очень раздражало, что вас заставили найти все места, где вы взаимодействуете с конкретными классами.

Решением этой проблемы является полиморфизм .

По сути, вам нужно реализовать функциональность в одном месте внутри конкретного класса. Все производные классы должны реализовывать этот метод, а в базовом классе должен быть абстрактный метод. В коде вы фактически вызываете этот абстрактный метод и получаете различные исполнения кода в производных классах.

Для решения вашей проблемы вам следует создать несколько методов:

Метод, который возвращает все возможные свойства, которые этот класс может изменить.
Метод, принимающий строку, представляющую свойство, которое класс может изменить, и его новое значение.
Метод, который принимает строковое представление свойства и возвращает значение этого свойства.
После этого вам не нужны никакие логические обходные пути и приведения типов; код будет красивым и чистым.

Также на этом этапе следует реализовать сохранение в файл и загрузку из файла. Вы можете сохранить контакты, используя сериализацию. Вам следует указать файл, с которым вы работаете, с помощью аргумента командной строки. Это позволит автоматически сохранять контакты на жестком диске после каждого действия, изменяющего данные. Если вы не укажете аргумент, вам следует создать новые контакты и сохранить их в памяти. Если вы укажете несуществующий файл, вам следует создать пустой «Контакты» и сохранить все изменения во вновь созданном файле.

Также на этом этапе вам следует реализовать функцию поиска. Для этого вы можете добавить все значения из всех свойств и проверить, содержит ли эта строка поисковый запрос. Он также должен поддерживать регулярные выражения! И, конечно же, оно должно быть нечувствительно к регистру.

Используйте пустую строку для разделения различных действий, как в примере.

Пример
Ниже приведен пример того, как может выглядеть ваш результат. Символ > представляет ввод пользователя.

open phonebook.db

[menu] Enter action (add, list, search, count, exit): > count
The Phone Book has 6 records.

[menu] Enter action (add, list, search, count, exit): > search
Enter search query: > cent
Found 3 results:
1. Central Bank
2. Centurion Adams
3. Decent Pizza Shop

[search] Enter action ([number], back, again): > again
Enter search query: > shop
Found 2 results:
1. Decent Pizza Shop
2. Car shop

[search] Enter action ([number], back, again): > 2
Organization name: Car shop
Address: Wall St. 3
Number: +0 (123) 456-789-9999
Time created: 2018-01-01T00:03
Time last edit: 2018-04-29T11:34

[record] Enter action (edit, delete, menu): > edit
Select a field (name, address, number): > name
Enter name: > New Car Shop
Saved
Organization name: New Car Shop
Address: Wall St. 3
Number: +0 (123) 456-789-9999
Time created: 2018-01-01T00:03
Time last edit: 2018-11-20T11:04

[record] Enter action (edit, delete, menu): > menu

[menu] Enter action (add, list, search, count, exit): > search
Enter search query: > new
Found 1 result:
1. New Car Shop

[search] Enter action ([number], back, again): > back

[menu] Enter action (add, list, search, count, exit): > list
1. New Car Shop
2. Decent Pizza Shop
3. Central Bank
4. Centurion Adams
5. John Smith
6. Alice Wonderlanded

[list] Enter action ([number], back): > 6
Name: Alice
Surname: Wonderlanded
Birth date: [no data]
Gender: F
Number: +123123 (123) 12-23-34-45
Time created: 2018-03-12T11:21
Time last edit: 2018-03-12T11:21

[record] Enter action (edit, delete, menu): > edit
Select a field (name, surname, birth, gender, number): > number
Enter number: > +23 (321) 12-12 12 12
Saved
Name: Alice
Surname: Wonderlanded
Birth date: [no data]
Gender: F
Number: +23 (321) 12-12 12 12
Time created: 2018-03-12T11:21
Time last edit: 2018-11-20T11:07

[record] Enter action (edit, delete, menu): > menu

[menu] Enter action (add, list, search, count, exit): > exit
