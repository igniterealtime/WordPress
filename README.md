# Openfire Social
Provides social network with member profiles, activity streams, user groups, messaging, blogs and more by integrating Openfire Meetings and ConverseJS with  WordPress, bbPress and BuddyPress.

<img src="https://igniterealtime.github.io/Openfire-Social/openfire-social.png" />

# How it works
- Openfire shares same MySQL DB with WordPress and uses the DB Auth, User and Group providersto share same data.
- Requres PHP to be installed and configured for Jetty FastCGIProxyServlet as normally done for an external web server like Nginx.
- Openfire hosts pre-configured WordPress web application plus plugins in Jetty instead of Apache or Nginx.

# What you need
- MySQL or compatible DB
- PHP-fpm or PHP-CGI. 
Edit /etc/php-fpm.d/www.conf file as needed, ensuring that PHP-fpm is listening on localhost:9000 and the user under which it runs matches your openfire user.
- Openfire 3.4.0 or higher configured and working with MySQL DB. You **cannot** use the embedded db
- The Openfire Meetings plugins for Openfire.
- The Bookmarks plugin for Openfire
- The HTTP File Upload plugin for Openfire

# How to Install
- Deploy Openfire Meetings and all other openfire plugins. Configure accordingly. <b>Do not change</b> the context path for ofmeet to "/".
- Deploy the wordpress.jar file from the [release pages here](https://github.com/igniterealtime/Openfire-Social/releases/tag/v0.0.2) in Openfire as a normal plugin
- First go to https://yourserver:7443/info.php to confirm PHP PHP-fpm gateway is working and Jetty can serve PHP from Openfire
- Then go to https://yourserver:7443/wp-admin to setup wordpress in the same MySQL DB as Openfire
- When prompted for username/password, use the admin user in openfire to continue
- Activate and configure all 5 pre-installed wordpress plugins.
- Create some users, groups and forums to confirm Wordpress is working fine with Jetty Web server in Openfire

Now you are ready to add converseJS chat with wordpress. Do the following
- Edit the file OPENFIRE_HOME/plugins/wordpress/classes/converse/core/index.js to changes the default converse configuration if you need to.
- Go to Openfire web admin server|wordpress web page and enable auth, user and group provider check boxes. 
- Go to plugins web page and restart the wordpress plugin.
- When wordpress restarts, it will cause openfire to switch to wordpress for all users and groups data.
- Go to Users/Groups web page to confirm this.
- You are now ready to test users with converse and wordpress together

# How to use
- To login to to https://yourserver:7443/index.html
- When prompted for username/password, use any of the users created in wordpress
- if all goes well, you should have your wordpress homepage with converse chat button in bottom right corner. Click on it to login


