# bank_project
Краткое описание: "Нашим проектом является банк, в котором находится пользователи, которые имеются свои денежные средства в нашем банке, с которыми можно проводить операции
просмотра счетов, их снятия и их пополнения."


Принцип работы: "Наш код состоит из 5 классов, один из которых является основным. 

В классе User хранится информация о пользователя, т.е его ИМЯ, ФАМИЛИЯ, НОМЕР ТЕЛЕФОНА, ПАРОЛЬ и КОШЕЛЕК и методы для получения и изменения данных field. 

В классе Wallet хранится информация о кошельке пользователя. Кошелек пользователя состоит из 3 частей: ОСНОВНОГО СЧЕТА, ДЕПОЗИТА и КРЕДИТА. Для них также имеются 
методы для получения и изменения field.

Оба этих класса имеют ИЗМЕНЕННЫЙ МЕТОД toString(), для более удобного вывода информации о объекте через System.out.println.

В классе Bank хранится информация о всех имеющихся пользователей внутри банка, т.е. информация о каждом пользователя(БАНК РАБОТАЕТ НА ПОДОБИИ БАЗЫ ДАННЫХ).
В нем также можно обновлять массив пользователей через метод SET и получать сам массив вне класса через GET в виде целого массива.

В классе Validator хранится метод для проверки введеннего пользователя, чтоб при входе банк, он не давал доступ третьим лицам, не являющимся этим пользователем.

В метод checker(User user, User[] users) вводится пользователь, который должен пройти проверку и массив пользователей, хранящийся в банке. С помощью цикла, каждое поле введенного пользователя сравнивается с полями каждого пользователя, хранящегося в банке. Если данный метод, найдет хотя бы одного точно такого же пользователя, то он выдаст TRUE, что означает, что данный пользователь зарегистрирован в банке. В обратном случае он будет выдавать FALSE.

В классе Main уже происходит все взаимодействие с классами. 

Первый этап это ввод нескольких пользователей, которые потом объединяются в общий массив. После чего создается объект Bank, в чей конструктор вписывается массив пользователей для создания локальной базы данных, с которой будет идти дальнейшая работа.
Потом создается сразу объект Validator, поскольку дальше будет авторизация пользователя внутри банка, где понадобится метод checker.
Дальше запрашивается ввод информации о пользователи для его авторизации, с помощью создания объекта Scanner, внутрь которого вписывается любой системный инпут через 
System.in. Создается переменная boolean a = false, объект usercheck(проверяемый пользователь) с пустым конструктором, и цикл while(!a) через который будет проходить 
пользователь. 

Сначала вводится ИМЯ, ФАМИЛИЯ, НОМЕР ТЕЛЕФОНА и ПАРОЛЬ пользователя, потом все данные значения полей установливаются через методы SET в объект usercheck,
который является пользователем введенным в данный момент. После чего данный пользователь проходит if/else условие, в котором переменная boolean a изменится на true 
и закончит повторение цикла ввода пользователя и пойдет дальше, лишь в том случае, если validator через метод checker, в который мы введем пользователя, вернет значение 
true, иначе будет повторный запрос с ввода с сообщением "Нет такого пользователя!". 

Второй этап это уже работа с авторизованным пользователем. Сначала запрашивается выбор счета(ОСНОВНОЙ СЧЕТ, ДЕПОЗИТ, КРЕДИТ), с которым будет идти дальнейшая работа.
Дальше запрашивается выбор операции(ПОКАЗАТЬ СЧЕТ, СНЯТЬ ДЕНЬГИ И ВНЕСТИ ДЕНЬГИ), которая будет происходить с выбранным счетом. Через if/else условие,
происходит работа с Wallet, которая по умолчанию у всех созданных пользователей равняется значению 500 ПО КАЖДОМУ СЧЕТУ. 

При выборе ЛЮБОЙ ОПЕРАЦИИ, код просто 
выводит информацию о счете через SOUT(usercheck.getWallet()). Различия лишь в том, что при выборе СНЯТЬ ДЕНЬГИ, он сначала отнимает изначальное значение на счету и 
изменяет его через setWallet(), после чего происходит SOUT, а при выборе же ВНЕСТИ ДЕНЬГИ, все работает с точностью наоборот, так как изначальное значение 
на счету уже плюсуется. После этого работа кода закончивается и он останавливается.

Примечание 1: "В случае с КРЕДИТАМИ, при ВНЕСТИ ДЕНЬГИ идет плюсование значение, поскольку ЧАСТЬ КРЕДИТА оплачивается. А при снятии 
КРЕДИТА  он наоборот увеличивается, потому что пользователь берет большую сумму в долг"

Примечание 2: "Также при СНЯТИИ ДЕНЕГ введенное значение проходит через if/else условие, поскольку, если снимаемая сумма будет выше имеющийся, выведется сообщение
'Недостаточно средств на счету!'"
