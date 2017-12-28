# How do I install Decidim? 

## Step by step

We're starting with an Ubuntu 16.05 LTS. 

### Installing rbenv 

First we're going to install rbenv, for managing various ruby versions. We're following the guide from [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-ubuntu-16-04).

```bash
sudo apt-get update
sudo apt-get install -y build-essential autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm3 libgdbm-dev
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc
git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
rbenv install 2.3.1
rbenv global 2.3.1
echo "gem: --no-document" > ~/.gemrc
gem install bundler
```

### Installing PostgreSQL 

Now we're going to install PostgreSQL for the database: 

```bash
sudo apt-get install -y postgresql libpq-dev
sudo su - postgres 
psql 
> CREATE USER decidim_app WITH CREATEROLE SUPERUSER CREATEDB; 
> \password decidim_app 
```

You need to enter a password (two times) and save it somewhere to configure it later with the application. 

### Installing Decidim 

Next, we need to install the `decidim` gem:

```bash 
gem install decidim
```

Afterwards, we can create an application with the nice `decidim` executable:

```bash
decidim decidim_application
cd decidim_application
bundle install
```

### Configure the database

For configuring the database you need to put the `config/database.yml`


### Initializing your app for local development

We should now setup your database:

```bash
bin/rails db:create db:migrate db:seed
```

This will also create some default data so you can start testing the app:

* A `Decidim::System::Admin` with email `system@example.org` and password `decidim123456`, to log in at `/system`.
* A `Decidim::Organization` named `Decidim Staging`. You probably want to change its name and hostname to match your needs.
* A `Decidim::User` acting as an admin for the organization, with email `admin@example.org` and password `decidim123456`.
* A `Decidim::User` that also belongs to the organization but it's a regular user, with email `user@example.org` and password `decidim123456`.

This data won't be created in production environments, if you still want to do it, run:

```bash
SEED=true rails db:setup
```

You can now start your server!

```bash
bin/rails s
```

Visit [http://localhost:3000](http://localhost:3000) to see your app running. 🎉 🎉