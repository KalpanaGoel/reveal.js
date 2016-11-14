# Entity API
Note:
- Welcome everyone!



## Kalpana Goel
## http://drupal.org/u/kgoel
## http://twitter.com/kalpanagoel
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
- We are back to our original question.. what is entity?
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
- like configuration entities (example - views, content types, vocabularies)
- Configuration entity supports translation.
- Content entity consists of configurable and base fields, can have revisions and supports translation.




# Entity Handlers
## Storage Handler
Note:
- What are handlers?
- Entities are supported by handlers.
- Storage handler supports loading, saving, and deleting entities.
- Storage handlers include default support for revisions, translations, and configurable fields.
- Does storage handler only support content entity since it includes support for revisions snd configurable fields.



## Check
## <img src="custom/images/entitycheck.png">
Note:
- Entity API in D8 is powerful
- It allows us to run different checks
- You can run check to make sure if an object is an entity
- If it is a content entity
- You can get the entity type
- Check if it is a node
- Explain the last one?




## Entity methods
## <img src="custom/images/entitymethods.png">
Note:
- There are a number of generic methods are available to get information from an entity
- You can get the ID
- get bundle
- Check if entity is new
- get the label of entity
- Create a duplicate that can be saved as a new entity



## Custom entity
### Blog content type
### <pre><code>
   name: Blog <br />
   type: module <br />
   core: 8.x <br />
</pre></code>
Note:
- We are creating blog content type as a custom entity
- First step... create folder modules/blog
- create blog.info.yml



## Entity class
## <img src="custom/images/entityclass.png">
## <pre><code>
<?php

namespace Drupal\blog\Entity;

use Drupal\Core\Entity\ContentEntityBase;

Class Blog extends ContentEntityBase {


} </code></pre>
Note:
- Blog entity is instance of the entity class
- entity class in d8 resides in modules/<module_name>/src folder
- We have blog entity in src folder
- In d8, src directory has all OOP code like class, interfaces, traits
- Procedural code is in .module file outside src directory
- We have /src/Entity/Blog.php
- Let's take a look at the code
- We have namespace which allows code from different frameworks like Symfony, Drupal
- Namespace has multiple parts. All classes in core and modules have Drupal as top level namespace
- second part contain name of the module
- third part corresponds to the folder inside src folder



## https://api.drupal.org/api/drupal/core%21core.api.php/group/oo_conventions/8.2.x
Note:
- Follow the link to see OOP conventions in Drupal 8.2.x


## Annotations
## <img src="custom/images/entityannotations.png">
Note:
- Annotations provides metadata about the code.
- As you can see annotations are part of comment but they are required for the entity type to function
- Let's take a look
- ID is ID of the entity type which is needed.
- Provided different labels for different possible usages
- Along with the label, we have provided storage information in base table
- We are providing database table we want blog data to be stored.
- ID and UUID are database columns



## https://api.drupal.org/api/drupal/core%21core.api.php/group/annotation/8.2.x
Note:
- Link if you would like to read more about annotations.



## Install blog entity
## <pre><code> drush entity-updates </code></pre>
Note:
- We have our blog entity class and annotations
- Let's install blog entity
- by running this drush command, drupal will crate database schema for our blog entity
- If you check db, you will see blog table in the database.



## Create and save blog
## <pre> <code>
use Drupal\blog\Entity\Blog;

$blog = Blog::create();
$blog->save();
</code></pre>
Note:
- for creating, saving, deleting entity type, we are going to use drush
- You can either use drush core-cli or create a test.php script and then running drush php-script test.php
- This command creates new blog entity in db and you will see a new row with id and uuid
- Let's explore the code
- Blog class inherits create and save method from ContentEntityBase
- These methods can be inherited without being present in the Blog class
- create is a static method and it is called by using the class name and ::syntax
- save is not a static method so it is used with instance of the class and -> syntax



## Load blog
## <pre><code>
use Drupal\blog\Entity\Blog;

$blog = Blog::load(1);
$blog->id();
$blog->uuid();
</code></pre>
Note:
- loading blog entity from db



## Delete blog
## <pre><code>
use Drupal\blog\Entity\Blog;

$blog = Blog::load(1);
$blog->delete();
</code></pre>
Note:
- Deleting blog will result in deleting record from db



## Add fields
## <pre><code>
use Drupal\Core\Entity\EntityTypeInterface;
use Drupal\Core\Field\BaseFieldDefinition;

public static function baseFieldDefinitions(EntityTypeInterface $entity_type) {
  // Get field definitions for 'id' and 'uuid' from the parent.
  $fields = parent::baseFieldDefinitions($entity_type);
</code></pre>
Note:
- Let's add some fields to blog entity
- We have the following code in /src/Entity/Blog.php
- We are using type hint in the method EntityTypeInterface $entity_type
- EntityTypeInterface is type hint. Type hint indicates what type of parameter should be passed in the function
- Our blog class is extending ContentEntityBase which has baseFieldDefinitions method
- this method provides id and uuid fields.



## code...
## <pre><code>
 $fields['title'] = BaseFieldDefinition::create('string')
    ->setLabel(t('Title'))
    ->setRequired(TRUE);

  $fields['description'] = BaseFieldDefinition::create('text_long')
    ->setLabel(t('Description'));

  $fields['published'] = BaseFieldDefinition::create('boolean')
    ->setLabel(t('Published'))
    ->setDefaultValue(FALSE);

  return $fields;
}
</code></pre>
Note:
- continuation of code
- As you can see... we are adding title, description and published fields
- Passing static create method to create fields
- chaining method?




## https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Core%21Field%21Annotation%21FieldType.php/class/annotations/FieldType/8.2.x
Note:
- List of all field types in Drupal 8 core




## Install fields
## <pre><code>
drush entity-updates
</code></pre>
Note:
- We have added fields to our blog entity
- let's install fields
- After running drush command, you will see title, description and published column in blog table.





