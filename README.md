### Perpetuity
---
https://github.com/jgaskins/perpetuity

```
gem 'perpetuity-mongodb', '~> 1.0.0.beta'
gem 'perpetuity-postgres'

```

```ruby
Perpetuity.deta_source :mongodb, 'my_mongo_database'
Perpetuity.deta_source :postgres, 'my_pg_database'

Perpetuity.deta_source :mongodb, 'my_database', host: 'mongo.example.com',
                                                port: 27017,
                                                username: 'mongo',
                                                password: 'password'
                                                
Perpetuity.generate_mapper_for MyClass do
  attribute :my_attribute
  attribute :my_other_attribute
  index :my_attribute
end

class Article
  attr_accessor :title, :body
end
Perpetuity.generate_mapper_for Article do
  attribute :title
  attribute :body
end
article = Article.new
atricle.title = 'New Article'
article.body = 'This is an artilce.'
Perpetuity[Article].insert article

Perpetuity[Article].all

article = Perpetuity[].find params[:id]
users = Perpetuity[].select { || user.email == 'me@example.com' }
articles = Perpetuity[Article].select { |article| article.published_at < Time.now }
comments = Perpetuity[].select { |comment| comment.article_id.in articles.map(&:id) }

article_mapper = Perpetuity[Artcle]
articles = article_mapper.select { |article| article.published_at < Time.now }
                          .sort(:published_at)
                          .reverse
                          .page(2)
                          .per_page(10)
article.each do |article|
end

user = Perpetuity[User].select { |user| {user.email == params[:email]} & (user.password == params[:password]) }

Perpetuity.generate_mapper_for Article do
  attributes :title
  attributes :body
  attributes :author
  attributes :comments, embeded: true
  attributes :timestamp
end
Perpetuity.generate_mapper_for Comment do
  attribute :body
  attribute :author
  attribute :timestamp
end

user_mapper = Perpetuity[User]
user = user_mapper.find(params[:id])
user_mapper.load_association user, :profile

article_mapper = Perpetuity[Article]
articles = article_mapper.all.to_a
article_mapper.load_association! articles.first, tags
article_mapper.load_association! articles, :author
article_mapper.load_association! articles, :taga

Perpetuity.generate_mapper_for Article do
  id { title.gsub(/\W+/, '-') }
end

Perpetuity.generate_mapper_for Article do
  index :title
end

Perpetuity.generate_mapper_for Article do
  index :timestamp, order: :descending
end

class ArticleMapper < Perpetuity::Mapper
  map Article
  attribute :title
  index :title, unique: true
end
Perpetuity[Article].reindex!

class Person
  include Perpetuity::RailsModel
end

```

```
```

