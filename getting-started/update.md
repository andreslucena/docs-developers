# Keeping your app up-to-date

We keep releasing new versions of Decidim. In order to get the latest one, update your dependencies:

```
$ bundle update decidim
```

And make sure you get all the latest migrations:

```
$ bin/rails decidim:upgrade
$ bin/rails db:migrate
```

You can also make sure new translations are complete for all languages in your application with:

```
$ bin/rails decidim:check_locales
```

Be aware that this task might not be able to detect everything, so make sure you also manually check your application before upgrading.