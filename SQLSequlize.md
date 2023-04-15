# SQL | Sequelize-cli

#### Полезные ссылки
| [sequelize.org](https://sequelize.org/docs/v6/core-concepts/assocs/) |
| :------------------:|
| [SQL Cheat Sheet](https://www.sqltutorial.org/sql-cheat-sheet/) |
| [Sequelize intro (Юля)](https://github.com/jtarasova/sequelize_intro) |
| [Памятка/шпаргалка по SQL](https://habr.com/ru/articles/564390/) |
| [27 распространённых вопросов](https://tproger.ru/articles/sql-interview-questions/) |

---
### Команды для терминала
```SQL
 • psql postgres // открыть в терминале постгрес
 • \l - Получить список баз данных:
 • \c dbname - Выбрать базу:
 • \dt — список всех таблиц.
 • \d - просмотреть таблицы текущей БД
 • \d table — структура таблицы table.
 • \du — список всех пользователей и их привилегий.
 • \dt+ — список всех таблиц с описанием.
 • \dt *s* — список всех таблиц, содержащих s в имени.
 • \i FILE — выполнить команды из файла FILE.
 • \o FILE — сохранить результат запроса в файл FILE.
 • \a — переключение между режимами вывода: с/без выравнивания.
 • \? - Чтобы посмотреть весь список команд, введите
```

### sequelize-cli

```SQL
npx sequelize db:create // create database
--модели--

npx sequelize-cli model:generate --name User --attributes firstName:string,lastName:string,email:string
// generate model with attributes 

npx sequelize-cli db:migrate // migrate
npx sequelize-cli db:migrate:undo //эта команда вернет самую последнюю миграцию
npx sequelize-cli db:migrate:undo:all //вернуться к исходному состоянию, отменив все миграции

--сиды--
npx sequelize-cli seed:generate --name demo-user
npx sequelize-cli db:seed:all // seed
npx sequelize-cli db:seed:undo //отменить последний сид
npx sequelize-cli db:seed:undo --seed name-of-seed-as-in-data //отменить определенный сид
npx sequelize-cli db:seed:undo:all // отменить все сиды

так же добавить если нет в сидах к каждой записи
createdAt: new Date(),
updatedAt: new Date(),
```

### sequelize-cli init 

```js
sequelize-cli init 

1. npm install sequelize pg pg-hstore
3. npm i -D sequelize-cli //cli
4. создать файл .sequelizerc //Заполнить файл

	const path = require('path');
	 module.exports = {
	 'config': path.resolve('db','config', 'config.json'),
	 'models-path': path.resolve('db', 'models'),
	 'seeders-path': path.resolve('db', 'seeders'),
	 'migrations-path': path.resolve('db', 'migrations')
	 };
	 
5. npx sequelize-cli init //cli
6. Прописать данные БД в файле database.json //cli username, password, database, dialect
7. модели
8. Пример связи:

group_id: {
        type: Sequelize.INTEGER,
        references: {
          model: {
            tableName: 'Groups',
          },
          key: 'id',
        },
      },
      
9. npx sequelize-cli db:migrate
10. npx sequelize-cli db:seed:all
```

### 4 Associations

1. - The `HasOne` association
2. - The `BelongsTo` association
3. - The `HasMany` association
4. - The `BelongsToMany` association

### Пример

```js
в моделях надо указать ассоциацию 

который ссылается
static associate(models) {
      this.belongsTo(models.Jocky, { foreignKey: 'jockey_id' });
      this.belongsTo(models.Horse, { foreignKey: 'horse_id' });
      this.belongsTo(models.Race, { foreignKey: 'race_id' });
    }

на кого ссылаемся
static associate(models) {
      this.hasMany(models.Entries, { foreignKey: 'horse_id' });
    }
```
