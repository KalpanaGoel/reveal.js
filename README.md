# Entity API
Note:
- Welcome everyone!




# Kalpana Goel
## drupal.org/u/kgoel
## twitter.com/kalpanagoel
Note:
- Introduction
- Why I am giving this session?



# What is an Entity?
## https://en.wikipedia.org/wiki/Entity
Note:
- You might have used in Drupal 7 if you used Drupal in your project.
- Let's discuss first what is an entity as a refresher.
- As per wikipedia- Entity is something that exists as itself as a subject or object.
- Wikipedia link is here if anyone would like to read more about it.




# Types of Entity
## Nodes(content)
## Comments
## Files
## Taxonomy terms
## Vocabularies
## Users
## Custom entity
Note:
- In earlier version of Drupal, we used field api to create content type but now we can add fields to not only content type
- but we an add them to comment, taxonomy
- We have different types of entity.



## Bundles
## Fields
Note:
- Bundles are implementation of entity types to which fields can be attached.
- Bundles can be considered as sub content types.
- For example - article, news releases, blog are bundles of content(node) type.
- not all entities has bundle types like users
- Fields are reusable piece of content. You can create custom field, custom formats, widgets etc
- Fields can be attached to bundles or entities.



## Entity
## api.drupal.org/api/drupal/core!lib!Drupal!Core!Entity!entity.api.php/group/entity_api/8.2.x
Note:
- We are back to first slide again... what is entity?
- Entity is one instance of a particular entity type such as comment, taxonomy term, user or blog, article (bundles)
- Entity API was it's own module in Drupal 7
- Entity api is in Drupal 8 core.
- Link is for latest Drupal 8 core which is 8.2.x
- You can read more about entity at this link



# Entity Variants
## Configuration Entity
## Content Entity
Note:
- Entity type in cores comes in two variants
- Configuration entity is used in the configuration system.
- What is configuration? Configuration is a place to store information that you want to deploy from dev to prod
- like configuration entities (example - views, content types)
- Configuration entity supports translation.
- Content entity consists of configurable and base fields, can have revisions and supports translation.




# Entity Handlers
## Storage Handler
Note:
- What are handlers?
- Entities are supported by handlers.
- Storage handler supports loading, saving, and







## Don't mistake composer as a package manager
## Composer adds dependency in vendor folder inside your project
Note:
- Common mistakes about composer.
- Composer deals with packages and libraries but on the project level and not on global level
- How does it work?




# Download Composer
## https://getcomposer.org/download/
### Windows instructions  https://getcomposer.org/doc/00-intro.md
### Installer will put composer.phar in your working directory
Note:
- Download composer
- Follow instructions to download composer
- windows, Linux instruction for the download




### Run this command to run composer
## <pre><code> php composer.phar </code></pre>
### You can move composer.phar in your PATH
Note:
- After download, how can you run composer?
- Wouldn't it be nice just to type composer instead of long command
- caveat.... too much typing
- Let's fix it!
- let's move composer.phar to your path
- What is path and how to find it?




## Path
## Path is an environment variable
## Microsoft Windows, Unix like operating systems
## https://en.wikipedia.org/wiki/PATH_(variable)
Note:
- What is Path?
- Link to read more info on Path




## Where to find Path?
## In Unix
## /usr, /usr/bin, /usr/local/bin
Note:
- Where can you find path?
- They are usaully in /usr, /usr/bin, or /usr/local/bin folders in Unix like operating systems




## Windows
## C:\WINDOWS\system32
Note:
- in windows... try to find Path in the above folder




## Unix like systems
## <pre><code> mv composer.phar /usr/local/bin/composer </code></pre>
## Windows
## <pre><code> mv composer.phar C:\WINDOWS\system32 </code></pre>
Note:
- you can run this to move composer.phar to a directory that is in your path
- What is the command to move composer.phar to path?
- Try Windows command to move composer in Path
- It's easy and now you will see how easy to run composer from the command line




# You can run composer by just typing composer
## <pre><code> composer </code></pre>
## You will see a list of available composer commands
Note:
- What is short command to run composer?
- You don't have to type php composer.phar to run composer
- How do you make sure that composer is running on your machine?




### To start using composer, you need composer.json in your project
### Drupal 8 comes with composer.json and composer.lock files
### Composer writes the list of the exact versions it installed into .lock file
Note:
- What do you need to do in general to run composer on your project?
- Is Drupal 8 and 7 using composer? We will cover and I will provide a link to use composer for Drupal 7 and 8.
- We will get to folder structure of Drupal 8 bit later in the training.



## packagist.org
## Packagist is composer main repository which is basically a source which tells about package source
### <img src="custom/images/packagist.png">
Note:
- So far we have talked about composer.
- We downloaded composer, moved composer to Path to run it simply by typing composer.
- let's move on......
- What is packagist?
- Packagist is just a single directory that you want to download in your project





## Adding packages
<pre><code> "require": { "package_name" : "version" }, </code></pre>
### You can add packages by modifying composer.json file
### run composer update
### It will download the required library into vendor folder
Note:
- How do you add packages?
- What do you do after you have added packages?
- What does this specific package do to your project?





## To use Composer with Drupal 7
## use the repository url:https://packages.drupal.org/7
## To use Composer with Drupal 8
## use the repository url:https://packages.drupal.org/8




## https://packagist.drupal-composer.org/
## https://www.drupal.org/node/2718229
Note:
- Check packagist.drupal-composer.org for how to add modules, themes in your drupal 8 project
- packagist.drupal-composer.org is going to be deprecate.
- www.drupal.org/node/2718229 has more info




## https://packagist.org/packages/drupal/drupal
## https://github.com/drupal-composer/drupal-project
## <img src="custom/images/drupal-composer.png">
Note:
- You can use composer itself to download Drupal (hint for quiz 1 which is later)
- drupal/drupal uses Drupal itself as a template for the new site.
- drupal-composer/drupal-project provides default configuration that otherwise need to be added manually.
- Take a look at the comparison between the two
- Composer plugin to automatically downloading Drupal 8 scaffolding files example index.php, update.php





## Drupal Scaffold
## .htaccess, robot.txt, index.php, update.php
## https://packagist.org/packages/drupal-composer/drupal-scaffold
Note:
- Since we are at the point where we are discussing to download Drupal 8 using composer...lets look into Drupal Scaffold
- Some of the files that belong to Drupal are not in the core subdirectory.
- For example .htaccess, robot.txt, index.php, update.php
- These are referred as Drupal scaffold files.
- If you use drupal/drupal as a template for your new composer project, there will be no composer mechanism to update core
- However if you use drupal-project, it manages scaffold files by using https://packagist.org/packages/drupal-composer/drupal-scaffold
- There is vendor directory in Drupal 8 which has bunch of dependencies. It is recommended to move vendor folder outside Drupal root





## Quiz 1
Note:
- Alright, now the exciting part of the training.
- We have covered composer in-depth so far. Let's use what we have learned and apply that knowledge.



## Download Drupal 8
## Hint: Use Composer
Note:
- Find out the latest Drupal 8 core version
- Install latest Drupal 8 core on your machine (use composer)
- solution ...
- if using https://github.com/drupal-composer/drupal-project
- composer create-project drupal-composer/drupal-project:8.x-dev my_site_name-dir --stability dev --no-interaction
- This will download the drupal-composer/drupal-project project into a folder named my_site_name and then execute composer install.
- if you are using drupal/drupal
- composer create-project drupal/drupal my_site_name 8.2.*@dev
- This will download the drupal/drupal project into a folder named my_site_name and then execute composer install




## Woot!
## Drupal 8
Note:
- Y'all should have Drupal 8 installed on your machines now
- Woot!
- You did it!




## Check Drupal 8 folders, files
## Unix like systems
<pre> <code> las -lah </code> </pre>
Note:
- Let's open Drupal 8 directory
- run ls -lah on Unix like systems
- run list on Windows
- look out for .htaccess, update.php, index.php. robot.txt
- We talked about them before quiz and referred them as Drupal Scaffold files :)



## Drupal 8
### www.drupal.org/project/drupal/git-instructions
### Drupal 8 is on 8.2.x
### Currently Drupal 8 is on 8.2.x branch
### In Drupal 8 we have adopted semantic version controlling
### Drupal 8 is doing stable release every 6 month.
Note:
- All of us should already have Drupal 8 project and we used Composer to install drupal 8.
- There are other ways to download D8. Let's look into classic way of download drupal.
- What is Drupal.org?
- Is there any specific version of Drupal 8 available for download?
- How do I make sure which version of Drupal 8 core I need?
- Core version should already be selected to the latest version of D8
- What is the development and release cycle of Drupal 8?
- What is semantic version?




<pre><code>
git clone --branch 8.2.x https://git.drupal.org/project/drupal.git </pre></code>
### run the above command to clone Drupal 8 repo in your machine
### Could be download anywhere but prefer in Sites folder or projects
Note:
- We are looking into other ways to download Drupal 8 and other best way is to clone repo from drupal.org
- What is the command to clone repo for Drupal 8?
- What does repo mean?
- Where should I download the project?





<pre><code> cd drupal </pre></code>
<pre><code> ls </pre></code>
Note:
- I have a Drupal project.
- How can I see the content of the project?
- run "cd drupal" to navigate to drupal folder
- run "ls" to see the list of files, folders in D8
- We are going to comeback to this and talk about files and folders in D8




## Semver
### www.semver.org
### Drupal 8.2.x
### First digit is core version
### second digit indicates major version which backward compatible
### 3rd digit indicated minor version
Note:
- One thing I want to talk about now is Drupal version
- Drupal 8 is using semantic versioning.
- What is semvar?
- What does all this digit 8.2.x mean?
- Can it be 8.2.x.x and so on?




## www.drupal.org/node/1612910
### Read more about Drupal semantic version
### Benefits .... features doesn't have to wait to get in until next core release
Note:
- Is there any documentation on Drupal.org regarding semantic version?
- Does this exist in Drupal 7 or 6?
- Why did Drupal 8 adopt this?




## You have Composer and Drupal 8 installed and running
## WOOt!
## Let's shift gears and talk about Composer autoloading




## Composer autoloading
## Composer helps with the issues with autoloading in PHP, dependencies and where to put libraries
## <pre><code> require __DIR__ . '/vendor/autoload.php'; </code></pre>
Note:
- Let's continue and accomplish other things in our training!
- checkout composer autoloading
- what the heck is autoloading?




### Composer generates autoload.php into vendor directory
### Autoloading makes it easy to use third party code
### If your project depends on 3rd party library, you can start using its classes
and classes will be autoloaded
Note:
- what does it do and how does it work?
- Is there any advantage of using autoloading?



## <pre> <code>
"autoload": {
    "psr-4": {
        "Drupal\\Core\\Composer\\": "core/lib/Drupal/Core/Composer"
    }
},</code></pre>
Note:
- Is there any example to add composer? Lets take a look at this code...
- What the heck is PSR 4?
- Why am I seeing all this weird slashes and so many of them?
- Where did we get the code from? from composer.json
- Let's find answer to these questions.




###  Drupal added its own code to the autoloader by adding autofield in composer.json
### Composer will autoload PSR-4 autoloader for the Drupal\\Core\\Composer\\ namespace
### core/lib/Drupal/Core/Composer core folder will be put on the same level as vendor directory is
### Lets check core/lib/Drupal/Core/Composer and there is Composer.php which has Drupal\Core\Composer\ class
Note:
- What is this code doing?
- Drupal scaffold will generate autoload.php at the Drupal root to require composer generate autoload file
- Drupal added its own code to the autoloader by adding autofield
  in composer.json
- Composer will autoload PSR-4 autoloader for the Drupal\\Core\\Composer\\
    namespace
- core/lib/Drupal/Core/Composer core folder will be put on the same level as
      vendor directory is
- Lets check core/lib/Drupal/Core/Composer and there is Composer.php which has
 Drupal\Core\Composer\ class




## Topics we've covered so far
### Composer
### Download composer
### Download Drupal 8
### Composer autoloading
Note:
- We talked about composer, download composer, add to path file
- Downloaded Drupal 8 using composer
- Looked at Drupal 8 directory structure
- Talked about composer autoload.




## Scripts
## Scripts can either be a PHP Callback or command-line executable command.
## https://getcomposer.org/doc/articles/scripts.md
Note:
- Let's talk about scripts.
- Scripts are useful for executing package's custom code or package specific commands during the composer execution process.



## <pre><code>  "scripts": {
                  "pre-autoload-dump": "Drupal\\Core\\Composer\\Composer::preAutoloadDump",
                  "post-autoload-dump": "Drupal\\Core\\Composer\\Composer::ensureHtaccess"
                } </code></pre>
Note:
- This example is from Drupal 8 composer.json file
- In order to define scripts in composer.json file, root JSON object should have a property defined as scripts.
- We do have scripts in our composer.json file here.
- scripts contains pair of named events and each events corresponding scripts.
- Scripts execute in the order their event is fired.
- In our example... Drupal is adding vendor classes to composers static classmap on pre-autoload-dump event.




## General facts about scripts
### Script events can contain both PHP callback and command line executable commands.
### PHP classes containing callable methods must be autoloadable via composer's autoload functionality.
### Callbacks can only autoload classes from psr-0, psr-4 and classmap definitions.



## Command Events
## pre-install-cmd
## post-install-cmd
## post-update-cmd
Note:
- There are some command events available.
- Some importants are pre-install-cmd, post-install-cmd, post-update-cmd
- pre-install-cmd occurs before the install command is executed with a lock file present.
- post-install-cmd occurs after the command has been executed with a lock file present.
- post-update-cmd occurs after the update  or install command has been executed without a lock file present.



## Running Scripts
## <pre><code> composer run-script post-install-cmd</code></pre>
Note:
- To run the script manually, you can run commands like this.




### SSH
#### Cryptographic network protocol for operating network services securely
over an unsecured network
Note:
- Alright we now have composer, Drupal 8
- Let's discuss SSH briefly
- SSH stands for secure shell
- SSH provides a secure shell over unsecured network in a client-server
architecture connecting SSH client application with SSH server.




## Best use
## Remote login to computer systems by users
## Remote command execution
Note:
- There are some examples of use cases of running SSH



### SSH uses public-key cryptography to authenticate the remote computer
### Ways to use SSH
#### Use automatically generated public-private key pair to encrypt network
connection and use password authentication
#### Manually generated public-private key pair (no password required)



## Drush
## Drush stands for "The Drupal Shell"
## Drush code repo
## https://github.com/drush-ops/drush
## See test coverage in drush
## https://github.com/drush-ops/drush/blob/master/tests/README.md
## Drush is command line interface shell scripting tool for Drupal
## http://www.drush.org/en/master/
Note:
- What is Drush? Drush is command line interface shell scripting tool for Drupal
- Does it work with all versions of Drupal? Yes, it does.
- Does Drush work with core and contrib modules? Yes, it works with core, contrib and custom modules, themes.




## http://docs.drush.org/en/master/install-alternative/
## https://www.youtube.com/watch?v=eAtDaD8xz0Q&feature=youtu.be
## Install latest stable Drush
## <pre><code>composer global require drush/drush </code></pre>
## <pre><code>drush status</code></pre>
Note:
- We already have composer installed and working. let's use composer to install drush.
- You can watch the presentation in your spare time to install composer.
- In this command, we used composer to install drush.
- Run "drush status" to verify that you have working drush on your machine.




## For Windows users
## http://docs.drush.org/en/master/install-alternative/#windows
Note:
- There are few options to install drush.
- Either download Acquia DevDesktop which comes with Drush
- Or use some VM option




## Acquia DevDesktop
## https://dev.acquia.com/downloads
## Drupal VM
## https://www.drupalvm.com/
Note:
- As we discussed in previous slide, either use Acquia DevDesktop or use Drupal VM.




## Running drush commands
## https://drushcommands.com/
## Create your own custom drush commands
## https://www.chapterthree.com/blog/how-to-create-custom-drush-commands
Note:
- Drush commands site has some of most used drush commands that would be useful for your project
- You can read more on chapterthree site about creating custom drush commands




## Git
### Free Open source distributed version control system
### Robust version system
### Ways to learn
#### https://try.github.io/levels/1/challenges/1
#### https://www.codecademy.com/learn/learn-git
#### http://gitimmersion.com/
Note:
- Alright... composer, Drupal 8, Drush and let's move on to git.
- What is Git?
- What is version control system?
- What are the advantages of version control system?
- Is it explicit for Drupal?
- Do I have to use Git or can I use Drupal without it?





## Download Git
### www.git-scm.com/downloads
### www.git-scm.com/book/en/v2/Getting-Started-Installing-Git
Note:
- Download for perspective OS
- Where do I go to download Git?
- Are download steps different for Linux, Windows?




## First-time Git Setup
### Let's set up git on your machines
### Imagine everyone has a terminal (where you can type commands)
### Highly recommend iTerm2 on Mac
Note:
- How can I setup Git for the first time on my machine?
- What do I need to do to setup the Git?



## Setup your name
<pre><code> git config --global user.name "John Doe" </pre></code>
### Tell Git who you are!
### Replace "John Doe" with your name
Note:
- What commands do I need to run to set up git on my machine?
- Can I pick any name?
- How does it help when I provide my name?
- What's the purpose of providing my name?




## Setup your email
<pre><code> git config --global user.email johndoe@example.com </pre></code>
### It is important to set up your name and email
### Shows under git log after you commit something
### Whole point of version control
Note:
- What is the command to set up email?
- Why do I need to provide my email address?





## Check your config
<pre><code> git config --list </pre></code>
### Run git config --list in your terminal
### See Your name and email
### wohooo!
Note:
- Alright, I have provided my name and email address.
- Where can I check that I have provided correct info?
- Can I set my name and email again if it is incorrect or typo?





## Git help
<pre><code> git help </pre></code>
<pre><code> man git </pre></code>
### If you ever need help trying to figure out git commands
### Stackworkflow is your friend!
### Stackoverflow is not just for git but drush, Drupal, Symfony etc
Note:
- Ok, I have git installed, I have provided name and email address. Now what?
- Is there any documentation that I can see so I know what to do with Git?




## To initialize any project
<pre><code> git init </pre></code>
### To initialize any project run "git init" from the root of the project
### We are not going to run for Drupal 8 since it already has git integration
Note:
- How do I use Git in my project?
- Does my project or Drupal 8 already ships with git?




## PhpStorm
https://www.jetbrains.com/phpstorm/?fromMenu
Note:
- What is PhpStorm?
- PhpStorm is smart IDE
- perfect for working with Drupal, Symfony, Joomla etc.
- Free 30 day trial
- Prefer to buy
- finish installation




## Open Drupal 8 project
Note:
- How can I open the project in PhpStorm?
- Click on PhpStorm application
- Prompt for open or create project
- Open project and select your latest Drupal 8 project
- Voila!




## PhpStorm Customization
### <img src="custom/images/phpstorm-theme.png">
Note:
- Before we do anything, lets do some configurations in PhpStorm
- Preferences -> appearance -> theme
- Change it to Darcula
- Much better them then staring at white screen for hours
- Dark color goes easy on your eyes
- Language and preferences -> PHP-> Drupal (to integrate Drupal settings)
- Setup Drupal version
- Drupal coding standard will automatically applied if Drupal integration is
- selected.




## PhpStorm shortcuts
### For preferences (on Mac) command and comma
### On Windows, Linux - Ctrl ALT s
Note:
- press command and comma for preferences
- Check shortcuts under keymap
- You can change font size too



## .idea directory
Note:
- Phpstorm adds .idea directory by default
- right click on .idea folder and click exclude
- click on project and select project files



### Composer, Drupal 8
### Git, drush, SSh
### Phpstorm
Note:
- So far we have covered composer, Git, Drush
- We have also downloaded Drupal 8
- We have looked into PhpStorm and open our Drupal 8 project
- Does anyone have any question so far?
- Any comment, feedback?
- Is everyone feeling ok?
- Am I going too fast or slow?
- What's next? Symfony




# Symfony
## Symfony is a set of PHP Components, a web application framework.
## http://symfony.com/
Note:
- What is Symfony?



# What is Symfony framework?
## Leading PHP framework to create websites and web applications.
Note:
- Symfony framework consits of a toolbox (set of prefrabricated, rapidally integratable software components.
- Which means write less code, great productivity and devote more time to dedicate such as writing tests.
- The use of best practices gurantees the stability, maintainability and upgradability of your applications.
- A framework isn't necessary to build the web application
- It is one of the tools to help you develop better and faster
- Why better? Because it gives the certainity of developing an application in compliance with business rules
- It is maintainable, upgradable.
- Why faster? Because it allows developers to save time by re-using generic modules




# Why framework?
## Not having to reinvent the wheel!
## Upgradable and Maintainable
Note:
- The basic principle of framework.
- Someone has already doen the ground work for you so you don't have to.
- Rather spend your time in writing unit test for specific components
- Framework is upgradable and maintainable at lower cost



# Symfony components
## A set of decoupled and reusable components on which the applications are built.
Note:
- Symfony is built on top of a set of decoupled and reusable PHP components called symfony components
- You can choose any of Symfony components in your application independently from the framework.
- You can use composer to download Symfony components



# Symfony does use sematic version
# Deploy Symfony using platform.sh
# Install the installer to download Symfony
# We are going to mainly focus on Drupal 8
- Is there a core version in Symfony like Drupal?
- Does Symfony also has semantic version like Drupal?
- Can I use composer to download Symfony?
- Should I download Symfony for the purpose of this training?
- What are Symfony componenets? There are 34 components in Symfony
- Do I need to download each component? No, you don't need to download components



# Symfony Components used in Drupal 8
## BrowserKit
## https://symfony.com/doc/current/components/browser_kit.html
### Create a client
### Make Requests
### Clicking links
### Submitting forms
Note:
- Yeah!
- Drupal 8 is using quite some components of Symfony
- How did Drupal 8 decied to use which component?
- Can I learn about some other components of Symfony? - Of course, you can! symfony.com has quite a good documentation.
- You can download Symfony and play around with it.
- let's talk about components of Symfony in Drupal 8
- BrowserKit - It stimulates the behavior of web browser which makes it possible for you to make request, click on links, and submit form programmatically
- This only provides abstract client and not any backend ready to use HTTP layer.
- Basic usage of BrowserKit - You can create a client by extending class, making requests. We will talk about HTTPKernal later
- You can use request() to make HTTP requests.
- You can use BrowserKit component to click around the links (much more maybe for testing  to see  if you get the desired result)
- BrowserKit can also be used to fill the data and use submit() to send the data which makes HTTP POST request to submit the form data.




## ClassLoader
### https://symfony.com/doc/current/components/class_loader.html
### https://github.com/symfony/class-loader
### http://php.net/manual/en/language.oop5.autoload.php
Note:
- ClassLoader - provides tools to autoload your classes and cache their locations for performance.
- Whenever you reference a class in your code that has not been required or included yet, PHP uses autoloading mechanism
to delegate the loading of the class.
- What is autoloading mechanisim?
- Think a scenario.... You write a class for your OOP code and your class needs bunch of other classes and interfaces.
- This could be really annoying to include those classes/interfaces and create a long list of those in your class.
- PHP provides spl_autoload_register() function to autoload those required classes/interfaces to be automatically loaded.
- Symfony provides PSR-0 and PSR-4 class loader. Drupal 8 is using PSR-4.




## PSR
## PSR-0 http://www.php-fig.org/psr/psr-0/
## PSR-4 http://www.php-fig.org/psr/psr-4/
Note:
- Let's take a minute to talk about psr
- You can read more about psr-0 here http://www.php-fig.org/psr/psr-0/
- psr-0 is deprecated now.
- psr-4 describes the specification for autoloading classes from file paths.
- This psr also describes where to place files that will be autoloaded according to the specification.




## Console
### https://github.com/symfony/console
### https://symfony.com/doc/current/components/console.html
Note:
- github link is to read the code.
- What is a console?
- Console component allows you to create command-line commands.
- Some usage example.... use console commands to create commands for any recurring tasks such as cron jobs, imports and other batch jobs.
- Drupal Console project is using the same idea of Symfony Console which is very handy in the development of Drupal 8 sites.
- We will cover in-depth details about Drupal Console later in the training.



## CssSelector
### https://github.com/symfony/css-selector
### https://symfony.com/doc/current/components/css_selector.html
Note:
- CssSelector component converts CSS selectors to XPath expressions.
- Why do you want to use CssSelector?
- When you are building any web application and parsing HTML, the most powerful method is XPath.
- XPath expressions are flexible but there is a steep learning curve.
- Developers are comfortable using CSS selectors to find elements.
- CSS selectors are easier than XPath expressions but less powerful.
- CSS selectors can be converted into XPath.
- XPath can be used in other functions, classes to find elements in the document.



## <img src = "custom/images/CssSelector.png">
Note:
- let's take a look at this code. This example is from Symfony.
- CssSelector component goal is to convert CSS selectors to their XPath equivalents using toXPath().
- You can use XPath equivalents to find elements in a document.




## XPath
## http://api.symfony.com/3.1/Symfony/Component/CssSelector/CssSelectorConverter.html#method_toXPath
Note:
- You can read more about XPath at this link.
- You can add optional prefix to the resulting XPath expression.




## Debug
### https://github.com/symfony/debug
### https://symfony.com/doc/current/components/debug.html
Note:
- Debug component is used by Drupal Console project.
- Debug component provide tools to ease debugging PHP code.



## <img src="custom/images/debug.png">
Note:
- enable() registers an error handler.
- DOn't enable debug in the production environment to hide sensitive information from users.



## <img src="custom/images/errorhandler.png">
## <img src="custom/images/exceptionhandler.png">
Note:
- ErrorHandler class catches PHP errors and converts them to exception of ErrorException class or FatalErrorException for PHP fatal erros.
- You can also enable exception handler which catches PHP exceptions and converts them into nice PHP response.



## DependencyInjection
### https://github.com/symfony/dependency-injection
### https://symfony.com/doc/current/components/dependency_injection.html
Note:
- This component allows you to standardize and centralize the way objects are constructed in your application.




## Service Containers
### https://symfony.com/doc/current/service_container.html
Note:
- let's take a step back before we dig deeper into DI
- A modern PHP application (Drupal 8 project) is built on objects.
- One object does some stuff, other objects stores data related to the other object which is responsible of doing stuff.
- Modern application does many things and is organized into different objects that handle each unique task.
- Service container is a PHP object in Symfony which instantiate, oragnize and retrieve objects of your application.
- Drupal 8 and Symfony uses service containers extensively.
- First talk about service....A service is a PHP object which performs some sort of global task.
- PHP object is a service if it is used globally in your application.
- Since each service does one job, you can easily access service and use its functionality wherever you need it.
- Service can be easily configured and tested because it is separated from other functionality in your application.
- Let's talk about service containers
- Service container is simply a PHP object that manages the instantiation of services.




## <img src="custom/images/mailer.png">
Note:
- Let's take a look at this
- In this example...Here we have a PHP class that delivers email messages.
- It's easy and perfectly fine.
- Mailer class allows to configure the method to deliver email messages.
- What if you want to use this method somewhere else then you need to write the same lines of code again.
- Repetitive code which does same thing in your application isn't the best practice.
- What if you need to change Mailer object to change to something else everywhere in the application.
- How do you avoid all this chaos? Answer is service container



## <img src="custom/images/mailer-service.png">
Note:
- An answer to the problem we discussed previously is service container
- Let service container create Mailer object for you
- In the example, you define service container, class and arguement/s
- Service creatation/configuration is done in YAML file



## <img src="custom/images/mailer-class.png">

Note:
- An instance of the class defined in service container is available via service container
- Service container is available in controller class where you can access the service of the container
- We will discuss Controllers later in the training.
- Container constructs the object and returns it.
- Service is goog from efficiency point of view as it is not constructed until it is needed
- Using services is good for performance as it is never created if it is never used.
- Having too many services don't slow down your application for this specific reason.




## Service Parameters
## <img src="custom/images/service-parameters.png">
Note:
- Let's take a look at this code
- If you notice... previous service container code is exactly same as this one except percent(%) sign in the arguments
- Purpose of using parameters is to feed information into services.
- Using parameters allows the service to be easily customized.



## Example of Service Parameter
## <img src="custom/images/service-parameter-example.png">
## <img src="custom/images/service-parameter-argument.png">
Note:
- You can pass "@" in the argument but it needs to be escaped by using another "@"
- The percent sign inside argument or parameter should be escaped by another percent sign.



## <img src="custom/images/service-parameter-array.png">
Note:
- Parameters can also contain array values.




## Read more about parameters
## https://symfony.com/doc/current/service_container/parameters.html#component-di-parameters-array
Note:
- You can read more about types of parameters at this link




## Injecting services
## <img src="custom/images/service-injection.png">
Note:
- We looked at simple example of single arguments which is easy to configure
- What about injecting one or more services into other service in the container?
- Check the code, @app.mailer tells the container to look for a service named app.mailer, to pass the object into the constructor of NewsletterManager
- Specified app.mailer service must exist and if it doesn't then exception will be thrown.




## Dependency Injection
Note:
- We are back to learn more about DI
- You know about service and service containers now. Let's see how those play with DI.





## DomCrawler
### https://github.com/symfony/dom-crawler
### https://symfony.com/doc/current/components/dom_crawler.html
Note:
- This Symfony component is used by Drupal Console project.
- This component eases DOM navigation for HTMl and XML documentation
- In other words, this class provides methods to query and manipulate HTMl documents.
- This crawler will attempt to automatically fix your HTML to match the official specification.
- For example - If you nest a <p> tag inside another <p>, it will be moved as a sibling of the parent tag.



## EventDispatcher
### https://github.com/symfony/event-dispatcher
### https://symfony.com/doc/current/components/event_dispatcher.html
Note:
- This component provide tools that allows your application components to communicate with each other by dispatching events and listening to them,
- Taking a step back before diving into this component
- Briefly covering what is a single inheritance..
- Single inheritance enables a class to inherit properties and behavior from a single parent class.
- To understand the concept behind EventDispatcher. Imagine you have a plugin system for your project.
- We will cover plugin later but briefly plugin is something that should be able to add methods, do something before or after the mehtod is executed without interferring with other plugins.
- This is not a easy problem to solve with single inheritance.
- Thats where EventDispatcher comes in handy.
- We will take an example of HttpKernel component.




## HttpKernel
### https://symfony.com/doc/current/components/http_kernel.html
Note:
- HttpKernel provides a structured process for converting a request object into response object by making use of EventDispatcher component.




## <img src="custom/images/01-workflow.png">
Note:
- Let's take a look at this image and talk about request and response in a web world.
- User requests for a resource in a browser and browser displays response to the user.
- There is sequence of workflow behind the scenes that takes place to process the request and display response in a browser.
- HttpKernel provides an interface that formalizes the process of starting with a request and creating the response.




## Httpkernel::handle()
## <img src="custom/images/httpkernel.png">
Note:
- This method works internally by dispatching events as it is mainly driven by events.
- Most of the work is done in event listeners.
- To use HttpKernel, it requires creating an EventDispatcher and a controller and argument resolver, add event listeners.
- In this code, there is EventDispatcher, controller, resolver.
- you will need to add EventListener.




##Event Listener
## https://symfony.com/doc/current/components/http_kernel.html#http-kernel-creating-listener
Note:
- You can create and attach event listener to any of the events dispatched during Httpkernel::handle cycle.



# Key Fact and Resource
## <img src="custom/images/new-httpkernel.png">
## https://symfony.com/doc/current/create_framework/introduction.html
Note:
- There are some changes in Httpkernel number of parameters.
- Check out the tutorial series on using HttpKernel component.




## kernel::request Event
## <img src="custom/images/kernel-request.png">
Note:
- kernel::request is the first event that gets dispatched in HttpKernel::handle which may have a variety of event listeners
- Listeners can be varied as some could be security listener which might create response immediately or it can redirect user to 403 by creating RedirectResponse if user shouldn't have access to content




## <img src="custom/images/03-kernel-request-response.png">
Note:
- You can see if response is returned at this stage, the process skips directly to kernel.response event.
- Another common listener is "routing".
- Routing listener may process the request and determine the controller that should be rendered.
- Request object has an attributes bag that could store application specific data about the request.
- If a router listener determines the controller, that information could be stored on Request attributes which can be used by controller resolver.
- The purpose of kernel.request event is either create and return a response or add information to the request if necessary.




## <img src="custom/images/kernel-request-fact.png">
## http://api.symfony.com/3.1/Symfony/Component/HttpKernel/EventListener/RouterListener.html
Note:
- The most important listener to kernel.request in the Symfony network is the RouteListener.
- RouteListener initializes the context from the request and sets request attributes based on a matching route.
- RouteListener class executes the routing layer, which returns an array of the information about the matched request including the match _controller and placeholders in route's pattern.




## Resolve the Controller
## <img src="custom/images/04-resolve-controller.png">
Note:
- Let's assume that kernel.request listener was able to create a Response.
- Next step in Httpkernel is to determine and prepare (resolve) the controller.
- Controller is responsible for creating and returning the response for a specific page.
- How does your application determine which controller for a request is up to your application and it is determined by controller resolver.
- Controller resolver implements ControllerResolverInterface and it is one of the constructor arguments to Httpkernel.




## kernel.controller
## <img src="custom/images/06-kernel-controller.png">
Note:
- After the controller callable has been determined, Httpkernel::handle dispatches the kernel.controller event.
- Listeners to this event can completely change the controller callable.





## Calling the Controller
## <img src="custom/images/08-call-controller.png">
Note:
- In this step, HttpKernel::handle executes the controller.
- Controller's job is to prepare the response for the given resource.




## Response
## <img src="custom/images/09-controller-returns-response.png">
Note:
- This shows that controller returns a response.
- Hence that completes the job of the kernel.
- kernel.response modifies the response object before it is sent such as modify headers, adding cookies, or it could change the content of the response.




## kernel.view event
## <img src="custom/images/10-kernel-view.png">
Note:
- If the controller doesn't return any response, kernel dispatches another event kernel.view.
- The job of this event is to use the return value of the controller and prepare the response.
- A listener to this event then can use this data to generate the response.
- If no response is return after kernel.view event then an exception is thrown.




## kernel.terminate
## <img src="custom/images/kernel-terminate.png">
Note:
- The final event of Httpkernel process is kernal.terminate and it occurs after HttpKernel::handle method.
- You can see in the code kernel->terminate gets triggered after sending the response.
- This event is optional.




## Handling Exception
## <img src="custom/images/11-kernel-exception.png">
Note:
- If any exception is thrown inside HttpKernel::handle, kernel.exception is thrown.
- When any exception is thrown, the kernel.exception is dispatched so your system can respond to exception.
- For example... to generate a 404 page, you might want to throw special exception, add listener to this event that looks for exception and prepares a response for 404 page.




## Routing
## https://github.com/symfony/routing
## https://symfony.com/doc/current/components/routing.html
Note:
- The routing component maps request to set of configuration variables.
- To set a routing system, it needs 3 parts




## RouteCollection
## RequestContext
## UrlMatcher
Note:
- RouteCollection contains the route definitions
- RequestContext has information about the request
- UrlMatcher performs the matching of the request to a single route.
- We are going to cover routing in-depth in the next training session



## HttpFoundation
## https://github.com/symfony/http-foundation
## https://symfony.com/doc/current/components/http_foundation.html
Note:
- HttpFoundation component defines an object-oriented layer for the HTTP Specification.
- What the heck does it mean?
- In plain language... this component replaces default PHP global variables ($_GET, $_POST, $_FILEs, $_COOKIE, $_SESSION) and functions by object oriented layer.




## Process
## https://github.com/symfony/process
## https://symfony.com/doc/current/components/process.html
Note:
- This component executes commands in sub-processes.





## Serializer
## https://github.com/symfony/serializer
## https://symfony.com/doc/current/components/serializer.html
## <img src="custom/images/serializer_workflow.png">
Note:
- Serializer component turns objects into a specific format (JSON, YAML, XML) and other way around.
- In this image, encoders will turn specific objects into array and vice versa.
- Normalizer also turn specific objects into array and vice versa.
- Serialization is a useful tool to serialize and deserialize your objects.




## Translation
## https://github.com/symfony/translation
## https://symfony.com/doc/current/components/translation.html
Note:
- This component provides tools to internationlize your application.
-




## Validator
## https://github.com/symfony/validator
## https://symfony.com/doc/current/components/validator.html
## https://jcp.org/en/jsr/detail?id=303
## What is JSR-303 Bean?
Note:
- This component provides tools to validate values following the JSR-303 Bean validation specification
- JSR-303 Bean define meta-data model and API for JavaBean validation based on annotations.
- This validator component is based on two concepts
- 1. Constraints, which defines rules to be validated
- 2. Validators, which are the classes that contain actual validation logic.




## <img src="custom/images/validation.png">
## https://symfony.com/doc/current/components/validator/metadata.html
Note:
- This is an example code where code is for validation of a string which is at least 10 characters long.
- Also to note, $validator object can validate simple variables such as strings, numbers and arrays.
- It can't validate objects
- You can configure validator class to make it validate objects and reading more - https://symfony.com/doc/current/components/validator/metadata.html




## Yaml
## https://github.com/symfony/yaml
## https://symfony.com/doc/current/components/yaml.html
Note:
- Yaml component loads and dumps YAML files.
- Symfony YAML component parses YAML strings to convert them to PHP arrays.
- It can also parse PHP arrays into YAMl strings.
- Yaml is a great format for configuration files.





## Yaml Goodness
### Fast
### Parser
### Dump support
### Types support
### Full merge key support
Note:
- One of the goals of Symfony yaml is to find the balance between speed and features.
- It supports a real parser and it is able to parse large subset of yaml specification. Parser is pretty robust, easy to understand
- If there is any syntax error in yaml, library outputs the helpful message with filename and the line number where problem occured.
- Yaml also able to dump PHP arrays to Yaml with object support.
- yaml supports dates, integers, octals, booleans etc
- It provides full support for references, aliases, and full merge key.




## https://symfony.com/doc/current/components/yaml/yaml_format.html
Note:
- You can read about yaml format
- With this... we have explored all the components of symfony is being used in Drupal 8




## What we've covered so far
## BrowserKit
## ClassLoader
## Console
## CssSelector
## Debug
## DependencyInjection
## DomCrawler




## HttpKernel
## EventDispatcher
## HttpFoundation
## Process
## Routing
## Serializer
## Translation
## Validator
## Yaml




#### HTTP Cache




### Composer, Drush, Git
### Drupal 8
### Symfony Components
Note:
- This is what we have covered so far
- Does anyone have any questions or comments?




## Quiz 2

Note:
- Alright, now the exciting part of the training.



## Install YAML for Symfony
Note:
- Use composer to install Symfony component (yaml)
- implement a 10-line CLI script parsing and printing
e.g. core.services.yml : this demonstrates composer, PSR/4 autoloading, yaml,
and introduces a constantly used file in D8
