# Installation (short version) 

First of all, you need to install the `decidim` gem:

```
$ gem install decidim
```

Afterwards, you can create an application with the nice `decidim` executable:

```
$ decidim decidim_application
```

Once you've created it, you have a good old Decidim Vanilla Application, that works mostly as a Rails Vanilla Application where you can add your own or community modules,  change the look and feel, overrride Decidim's code, configure the deploy with your own architecture, your own verification, etc. 

For local development you should at least configure the database. We recommend using PostgreSQL, if you have any doubts regarding the installation you should keep reading this guide.  