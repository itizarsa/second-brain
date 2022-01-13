# Scratch

```jsx
db.users.find({ email: "saas@spritle.com"}).pretty()

db.googles.find({user_id: "9160"}).pretty()

db.errors.find({ error_message: "Get Business Accounts error"}).sort({ updatedAt: 1 }).pretty()

db.errors.find({}).sort({ updatedAt: -1 }).pretty()

```

# paid apps

```jsx
//Find queries
db.users.find().pretty()

db.users.find({ email : { $regex : ".@spritle.com.*" } }).pretty()

db.mycol.find({},{"title":1,_id:0}).sort({"title":-1})

db.freshdesks.find({ email: "nadine.white@wavecrest.eu"}).pretty()

db.errors.find({ error_message: "Freshdesk ticket create error", user_id: "5188"}).pretty()

//Update queries
db.users.updateOne({ user_id: "2520"}, { $set:{plan_type : "estate"}})

db.playstoreapps.update( { user_id:"" },{ $set : {user_id:""}})

//Delete queries
db.playstorereviews.deleteMany({ user_id :"3622", app_id :"com.prostudent"})

db.googlequestions.deleteMany({ user_id: "7064"})

db.users.deleteOne({ user_id: "1061"})

//Export
mongoexport --collection=users --db=fdplaystore --out=/root/fdplaystore.json --fields=user_id,user_name,organization_name,email,createdAt,updatedAt,ticket_create_success,ticket_create_failure

mongoexport --collection=freshdesks --db=fdplaystore --out=/root/fdplaystore-users.json --fields=user_id,subdomain

//Download Exported
scp -r root@188.166.75.206:/root/fdplaystore.json .
```

# monday

```jsx
db.Credentials.find().pretty()

db.Credentials.find({_id : ObjectId('609d7e772efd3528330c187f')}).pretty()

db.Credentials.find({freshSubdomain : "propaganda3"}).pretty()

db.Integration.find({integrationId : 43975032 }).pretty()

db.Integration.find({credentialsId : "609d8a122efd3528330c1889" }, {_id:0, integrationId:1, fdWebhookId:1, recipeId:1, fdWebhookIdUp:1}).pretty()
```

# mongo

```jsx
//Create User
db.createUser( { user: "arsa", pwd: 'qwerty!@3456', roles: [ { role: "readWrite", db: "freshdesk-monday" } ] } )

//Drop
db.dropDatabase()

//Create Collection
db.createCollection('googles')

//Insert Row
db.user.insert({ title: 'Post One', date: Date() })

//Insert Multiple Rows
db.posts.insertMany([ { title: 'Post One', date: Date() }, { title: 'Post Two', date: Date() } ])

//Sort Rows
# asc
db.posts.find().sort({ title: 1 }).pretty()
# desc
db.posts.find().sort({ title: -1 }).pretty()

//Count Rows
db.posts.find({ category: 'news' }).count()

//Limit Rows
db.posts.find().limit(2).pretty()

//Chaining
db.posts.find().limit(2).sort({ title: 1 }).pretty()

//Foreach
db.posts.find().forEach(function(doc) { print("Blog Post: " + doc.title) })

//Update Row
db.posts.update({ title: 'Post Two' }, { title: 'Post Two', date: Date() }, { upsert: true })

//Update Specific Field
db.posts.update({ title: 'Post Two' }, { $set: { body: 'Body for post 2' } })

//Increment Field ($inc)
db.posts.update({ title: 'Post Two' }, { $inc: { likes: 5 } })

//Rename Field
db.posts.update({ title: 'Post Two' }, { $rename: { likes: 'views' } })

//Delete Row
db.posts.remove({ title: 'Post Four' })

//Sub-Documents
db.posts.update({ title: 'Post One' }, { $set: { comments: [ { body: 'Comment One' } ] } })

//Find By Element in Array ($elemMatch)
db.posts.find({ comments: { $elemMatch: { user: 'Mary Williams' } } })

//Add Index
db.posts.createIndex({ title: 'text' })
```

# pyenv

```jsx
brew install pyenv

$ echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc

exec $SHELL

pyenv install --list

pyenv install version #install latest from list

pyenv global version #set latest version

which -a python

which python

python -V
```

# npm

```jsx
npx depcheck

major.minor.patch

caret (^)  ^3.9.2  3.*.*  - Breaking Changes

tilde (~)  ~3.9.2  3.9.*  - No Breaking Changes
```

# ls

```jsx
ls -1 --color=always --group-directories-first | tac
```

# rbenv

```jsx
[https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-macos](https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-macos)
```

# git

```jsx
git remote -v

git remote add origin git@code.spritle.com:freshdesk/google-business-reviews-dashboard.git

git remote set-url origin git@code.spritle.com:freshdesk/google-business-reviews-dashboard.git
```