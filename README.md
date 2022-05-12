# helpful-heroku-tips
A list of some helpful beginner tips for navigating Heroku as an aA student. 

## Table of Contents

 - [Heroku Postgres Add-on](https://github.com/whitnessme/helpful-heroku-tips#heroku-postgres-add-on)
     - [To "drop database" / Reset](https://github.com/whitnessme/helpful-heroku-tips#to-drop-database--reset)
- [Useful Manual Console Commands](https://github.com/whitnessme/helpful-heroku-tips#useful-manual-console-commands)

---

## Heroku Postgres Add-on
### To "drop database" / Reset:
Instead of removing the postgres add-on to completely wipe one's database, follow these instructions to drop all the data, leaving only the database.

1. **Click on the specific app you want to remove data and click on the *Resources* tab.** 
![heroku nav](https://user-images.githubusercontent.com/89945390/168140727-f38df5cd-1ea2-45a6-842c-a35e5f4cb6bd.png)

2. **Click on *Heroku Postgres.***
![Postgres add-on](https://user-images.githubusercontent.com/89945390/168141005-1e2cbe9c-01a1-4bbe-9c1b-2f7ba630f0c8.png)

3. **Navigate to the *Settings* tab and the option you want to click is *Reset Database*.**
![heroku-postgres-settings](https://user-images.githubusercontent.com/89945390/168155610-3878e39f-7858-4769-bd92-045049c0ea39.png)

*If you are using the starter that deploys to Heroku through Github actions, then you can just push as usual and it will migrate and seed for you.* 

## Useful Manual Console Commands
These are if you're **not** using the automatic Heroku deploy through Github actions. But can be useful if the Github actions aren't working as expected.
*(Pease put a question up in the question-channel if there's problems so TA's can figure out what's going on and provide tips for other students)*

```bash
heroku login
```

```bash
heroku container:login
```

```bash
heroku container:push web -a {NAME_OF_HEROKU_APP}
```

```bash
heroku container:release web -a {NAME_OF_HEROKU_APP}
```

```bash
heroku run -a {NAME_OF_HEROKU_APP} flask db upgrade
```

```bash
heroku run -a {NAME_OF_HEROKU_APP} flask seed all
```

[Back to top ⬆](https://github.com/whitnessme/helpful-heroku-tips#helpful-heroku-tips)
