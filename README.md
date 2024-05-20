# loop-challenge
Special LOOP-CHALLENGE rep

Hi,

I seem to have completed your challenge and you can rate it at this link: http://64.227.123.233/ (without https because I've built the environment from scratch and decided not to spend 20-30 minutes to do it).

Credentials:
link: http://64.227.123.233/user
user: admin
password: Pa55word!

#How I decided to go for solutions

1. I used a minimum of third-party resources, so I only installed two additional modules: devel and pathauto (I was annoyed by the standard node paths);
2. While I was going round and round (no clear criteria in the requirements), then I decided to make the custom event module itself portable. What I mean is that when installed, it adds the taxonomy terms (Artists) and fills in all the data. It also creates the content type from scratch and creates all the fields with data;
3. Basically you just need to copy the web/modules/custom/loop module to your clean drupal (10.x) and run it `drush en loop -y`;
4. This will set up all the terms and content type. Everything else I did by hand: setting up languages, paths, views for the overview and the service's REST (http://64.227.123.233/events/api);
5. The theme (looptheme) is inherited from the most basic theme (olivio) and I did almost nothing there except one template and style file;
6. The Event Web site (link) field has been extended by `hook_field_widget_complete_form_alter()`;
7. I decided to make a json file with artists into a vocabulary for taxonomy terms - I thought this was a good idea as they contain their own fields (like albums, genre, etc). And to the content type I used an entity reference;
8. All json data is filled in when the module is installed, and subsequently updated each time the cron job is run `drush core:cron`;
9. All other module's options placed mostly in .install and .module files;
10. Config split works well also.

#Quick Links

Module: web/modules/custom/loop
JSON placed: web/modules/custom/loop/src/artists/artists.JSON
Theme: web/themes/custom/looptheme
SQL dump: web/sql-dump/loop.sql
Login: http://64.227.123.233/user
Events Overview: http://64.227.123.233/Events
Single Event (example): http://64.227.123.233/events/what-am-i-chopped-liver
API: http://64.227.123.233/events/api
Artists Taxonomy: http://64.227.123.233/admin/structure/taxonomy/manage/loop_artists/overview
Event Node Type: http://64.227.123.233/admin/structure/types/manage/loop_event/fields
Event View: http://64.227.123.233/admin/structure/views/view/events_overview


#About estimations

I spent about 19 hours and 3 fits to realise all of this.
I didn't have any internal environment (it just so happened) and had to buy a Digital Ocean droplet to set up the environment there as well. This took up some of my important time.

Roughly, I did the following:

Basic configuration of local and external environments + git + checking **(3hrs estimated / 5hrs spended)**
Drupal initialisation (composer) and basic settings for translations, pages, paths **(1,5hrs estimated / 1hr spended)**
Init of the module and theme. Create install/uninstall/schema instructions for creating taxonomy terms and content types with fields **(4hrs estimated / 6hrs spended)**
Working with extension for Link field (targeting) **(1hr estimated / 2hrs spended)**
Creating a theme and verifying that the templating works for the Entity Type Event. Some styles. **(2hrs estimated / 3hrs spended)**
Creating and customising views for Overview page and REST **(1,5hrs estimated / 1hrs spended)**
Delivery and description of solutions (documentation) **(1hrs estimated / 1hrs spended)**

#Conclusion

Of course, it's not a perfect solution, but it's not a basic solution either.
I liked my approach of deploying everything inside the module and taking it back if needed.
It looks like a portable version for all your requirements. All you have to do by hand is customise translations, add content and views. But that can be solved as well, ahahahaha ))
I hope you enjoy it

Regards,
Eugene
