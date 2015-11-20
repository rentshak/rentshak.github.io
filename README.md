#Presentation Layer (Front-End) Development Roles

>There are a number of distinct roles in this paradigm. I've tried to break them apart as best I can with sweet titles. This may be updated as time goes by, or you may update it as well. We're versioned so DGAF. *If you're on the master branch you will need to create your own.*

_New branches can be nested by simply creating them at a sublocation such as jefrfranklin/develop. Benefit is that all of your branches can be nested together. Often used to group bugfixes, features, and change-requests across large teams._

*Awessembler*:
	|	The person in charge of HTML, templating, and sitemap creation
    |	Recommending _Assemble.io_ (comes with _Handlebars Helpers_ plus it's awesome)
    |	Look into _grunt-assemble-sitemap_
    |	_Yaml Front Matter (YFM)_ - like _JSON_ but way easier. It'll take 10 minutes to learn.

*Interaction Hero*:
	|	The person whose researches, designs, and maintains effective call to action (CTA) and form elements
    |	In essence, you would puts yourself in the "users' shoes" and think about what makes sense in term of navigation and guiding user input
    |	Collaborates with the *APICON* on connecting _Javascript_ and _AngularJS_ front and back matter
    |	Works to ensure that *user input is sanitized upon submit and not directly reflected back to user thereby creating an XSS attack vector*

*Sassmeister*:
	| 	The master of all @imports Sass and our main CSS architect
	| 	Ensures subtle and processor-friendly animations
	| 	Ensures @media queries work correctly
	| 	Maintains global variables and functions
    | 	Responsible for a majority of the responsive design (RD) aspect
    | 	Works with the *Interaction Hero* to make sure RD is fully covered with _Javascript_ when required

*APICON*:
    |	Creates and maintains _Angular_ `service`s (API connectivity) for Rentshak DBs and third party services (Google Maps, Yelp, etc.)
    |	Works with the *Interaction Hero* to make sure that the presentation layer (PL) that the user sees is `get`ting the correct data objects
    |	Works with the *Data Dynamo* to make sure the `post`s from the PL are validated and correct

*Data Dynamo*:
	|	Maintains _Parse.io_ DBaaS and associated stored procedures (SP) that aggregate data based on abstract API requests (e.g. GetShopInfo() -> SP uses `GUID`s to `JOIN` appropriate tables and spits out _only_ necessary data)
	|	Continuously (automated or manually) stress tests DB SPs to discover programmatic bottlenecks and processes of greatest concern in regards to speed and always-on reliability of DB calls
	|	Works with *APICON* to ensure *SQL Injection* security holes are patched via encoding and sanitation *before* being sent to the DB
    |   *Independently researches the risks associated with and methods of malicious SQL Injection*

*Buildo Baggins*:
    |   Gets input from all other team members in terms of what build tasks (_Grunt_ build tasks, if we are using _Assembly.io_) they need to be effective in their roles.
    |   Creates customized _Grunt_ tasks for members as well as a master build task, a development build task
    |   Creates and maintains some sort of `server` task both for `dist` and `dev` - while `dev` is most likely a `localhost` server spun up in _Browser Sync_ or _Express_, `dist` would likely post data to _Heroku_ or a similar hosting platform.
    |   Maintains `package.json` and other package files (e.g. `bower.json`) that we use to ensure they are up-to-date
    |   Regularly tests `grunt` tasks to ensure efficient operation and acting when necessary to speed up bottlenecks (e.g. using `options{respawn: false}` where appropriate)

-----------------
*Gittin\*\*\*\**:
    |   A role everyone needs to adopt: "gitting" good at _Git_.
    |   Download _Sourcetree_ by _Atlassian_ (Mac or Windows)
    |   Realize that the `master` branch *isn't what you should be working on*
    |   Realize that if you add a bunch of new files and make some serious changes to some _AngularJS_ code, you should *commit them separately*
    |   Realize that the _second_ you make progress on a specific task, *commit it and give it a short but meaningful message.* We can all read everyone's Git commit messages.
    |   Don't be afraid to tag your updates if you consider them significant. |   The *general rule* for version tagging is if you have *v0.1.0* - you have *zero epochal/critical changes* (like alpha release candidate reached or major breaking changes to older versions), you have *one major change* (like successfully connecting an _Angular_ `service` to a new API, and *zero minor changes* (like changing from _HTML_ tags with `data-attributes` to customer _Angular_ `directive`s)