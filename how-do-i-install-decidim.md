# How do I install Decidim? 

## Step by step
** TODO explain Ubuntu 16.04 LTS, sudo apt update && sudo apt install git / rbenv / postgres / etc**


First of all, you need to install the `decidim` gem:

```
$ gem install decidim
```

Afterwards, you can create an application with the nice `decidim` executable:

```
$ decidim decidim_application
$ cd decidim_application
$ bundle install
```

### Initializing your app for local development

You should now setup your database:

```
$ bin/rails db:create db:migrate db:seed
```

This will also create some default data so you can start testing the app:

* A `Decidim::System::Admin` with email `system@example.org` and password `decidim123456`, to log in at `/system`.
* A `Decidim::Organization` named `Decidim Staging`. You probably want to change its name and hostname to match your needs.
* A `Decidim::User` acting as an admin for the organization, with email `admin@example.org` and password `decidim123456`.
* A `Decidim::User` that also belongs to the organization but it's a regular user, with email `user@example.org` and password `decidim123456`.

This data won't be created in production environments, if you still want to do it, run:

```
$ SEED=true rails db:setup
```

You can now start your server!

```
$ bin/rails s
```

Visit [http://localhost:3000](http://localhost:3000) to see your app running.