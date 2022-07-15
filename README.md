![heroku banner](https://miro.medium.com/max/1400/1*hDtj_hzXAz7Gj5eLn3goYg.png)
# helpful-heroku-tips
A list of some helpful beginner tips for navigating Heroku as an aA student. 

## Table of Contents

 - [Heroku Postgres Add-on](https://github.com/whitnessme/helpful-heroku-tips#heroku-postgres-add-on)
     - [To "drop database" / Reset](https://github.com/whitnessme/helpful-heroku-tips#to-drop-database--reset)
     - [To "view and access database"](https://github.com/whitnessme/helpful-heroku-tips#to-viewaccess-heroku-postgres-database-using-the-heroku-cli)
         - [Useful psql commands](https://github.com/whitnessme/helpful-heroku-tips#useful-psql-commands)
         - [Useful SQL commands](https://github.com/whitnessme/helpful-heroku-tips#useful-sql-commands)
- [File Locations and Paths for Images](https://github.com/whitnessme/helpful-heroku-tips#file-locations-and-paths-for-images)
     - [For `img` tags](https://github.com/whitnessme/helpful-heroku-tips#for-img--tags-)
     - [For Using CSS property `background-image`](https://github.com/whitnessme/helpful-heroku-tips#for-using-css-property-background-image)
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

4. **Follow the instructions to complete the reset.** 

5. **Migrate & Seed again!** *If you are using the starter that deploys to Heroku through Github actions, then you can just push as usual and it will migrate and seed for you.* 

---

### To "view/access" Heroku Postgres Database Using the Heroku CLI

1. **Click on the specific app you want to access data and click on the *Resources* tab.** 
![heroku nav](https://user-images.githubusercontent.com/89945390/168140727-f38df5cd-1ea2-45a6-842c-a35e5f4cb6bd.png)

2. **Click on *Heroku Postgres.***
![Postgres add-on](https://user-images.githubusercontent.com/89945390/168141005-1e2cbe9c-01a1-4bbe-9c1b-2f7ba630f0c8.png)

3. **Navigate to the *Settings* tab and then click on *View Credentials*.**
![heroku-postgres-settings](https://user-images.githubusercontent.com/76798385/178045579-9f242e6e-45b1-4f66-9bd8-b4db477a906d.png)

4. **Copy and paste the Heroku CLI into your teminal**
![Screenshot 2022-07-08 140256](https://user-images.githubusercontent.com/76798385/178047829-49b6e306-ddc8-4f05-911c-6c533f18be95.png)

5. **You should now have access to view the database for the Heroku app. This is incredibly useful when you are migrating and seeding data for your tables and you want to ensure the database is what you expect it to look like.**

---

#### Useful psql commands
```
\c dbname	Switch connection to a new database
```
```
\l	List available databases
```
```
\dt	List available tables
```
```
\du	List all users and their assign roles
```
```
\q	Exit psql shell
```

---

#### Useful SQL commands
```
SELECT select_list FROM table_name;
```
```
SELECT select_list1, select_list2, select_list3 FROM table_name;
```
``` *For selecting all columns from the database, use asterisk(‘*’) as below:*
SELECT * FROM table_name;
```

---

## File Locations and Paths for Images
> Heroku can be quite picky on where it will read image files in your repo. Here are a couple of solutions I've used.

### For `<img />` tags: 🖼
1. **Create a `static` directory in the `public` file to hold your image files.**
```
react-app
├── ...
├── public
│   ├── static
|   |    └── // image files here
│   ├── favicon.ico
│   └── index.html
├── src
│   └── ...
└── ...
```
2. **In your JSX, make an `img` tag with an src linked to the specific file in `static`.**
    - Tailor how many `..`'s you need to get out of the component directories. 
```
<img alt="knight painting icon" className="user-icon" src="../../../../static/knight_painting_crop.png"></img>
```
*For the above, my `src` file structure looked like:*
```
src
├── components
│   ├── ...
│   ├── Dashboard
│   │   └── UserBar.js
│   └── ...
└── ...
```

---

### For Using CSS property `background-image`:
1. **Create an `images` directory in `src` to store the image files in:**
```
src
├── components
├── context
├── images
|    └── // image files here
└── ...
```
2. **Create a JSX div or other element to have the image as the background.**
    - This can be an empty div but remember to give it a height and width.
```
<div className='landing-page-container'>
            <pre className='welcome-msg'>{msg}</pre>
            <h4 className='slogan'>Flashcards for adventurers!</h4>
</div>
```
3. **Put the CSS property on the specific element.**
```
.landing-page-container {
    ... // code removed for brevity
    background-image: url("../../images/A_Young_Man_Reading_by_Candlelight.jpg");
}
```
*For the above, my `src` file structure looked like:*
```
src
├── components
│   ├── ...
│   ├── LandingPage
|   |   ├── index.js
│   │   └── LandingPage.css
│   └── ...
├── images
└── ...
```

---

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
```
heroku logs -a {NAME_OF_HEROKU_APP}
```
```
heroku restart && heroku pg:reset DATABASE --confirm {NAME_OF_HEROKU_APP}
```
```
heroku run -a {NAME_OF_HEROKU_APP} printenv
```
[Back to top ⬆](https://github.com/whitnessme/helpful-heroku-tips#helpful-heroku-tips)
