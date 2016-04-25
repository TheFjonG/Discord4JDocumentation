Getting Started
===============

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ in the Discord4J channel.

Requirements
------------

Discord4J requires you to have a registered Account or a bot account.
You can `register an account here`_.

Discord4J requires `Java`_ and `Java JDK`_ aswell.

`Git`_ & a Java IDE is optional but is recommended. `Eclipse`_ and `Intellij IDEA`_ are both excellent Java IDES.

It is highly recommended that you make a bot account for your application.

.. _register an account here: https://discordapp.com/register
.. _Java: http://www.java.com/en/
.. _Java JDK: http://www.oracle.com/technetwork/java/javase/downloads/index.html
.. _Git: https://git-scm.com/
.. _Eclipse: https://www.eclipse.org/downloads/
.. _Intellij IDEA: https://www.jetbrains.com/idea/
Making a bot account
--------------------

You can either get a bot account via CURL or via `Discord API Website`_.
If you're going with Discord's bot maker, then make an Application, then add the bot account afterwards. ;)

Otherwise, you can follow this CURL tutorial:

* Install Curl from `Curl's website`_

There are 2 ways of getting a bot account:

1. First you'll need 2 account registred at Discord. Your main and your bot account.
2. You'll only need 1 account registered at Discord. Your main account only.

If youre going with the second way: [A NAME FOR YOUR APPLICATION] will be the name of the bot.

Let's begin by making an application.

Run this via CMD or Terminal or go here:`Make an Application`_:

.. code-block:: Bash

	curl -H 'Authorization: [YOUR TOKEN]' \
	-H "Content-Type: application/json" \
	-X POST -d '{"name": "[A NAME FOR YOUR APPLICATION]"}' \
	https://discordapp.com/api/oauth2/applications

You should get a response like this:

.. code-block:: Bash

	{"secret": "XXX", "redirect_uris": [], "description": "", "name": "THE NAME OF THE APPLICATION", "id": "YYY", "icon": null}

Keep the 'secret' and the 'ID' safe.
You have now succesfully created an application!

Now you want to make the bot itself.
Run this via CMD or Terminal:

.. code-block:: Bash

	curl -H 'Authorization: [YOUR TOKEN]' \
    -H "Content-Type: application/json" \
    -X POST -d '{"token": "[YOUR BOTS USERS TOKEN] <- ( LEAVE EMPTY IF YOUR GOING WITH THE SECOND WAY )"}' \
    https://discordapp.com/api/oauth2/applications/[Your Application's ID]/bot

You should get a response like this:

.. code-block:: Bash

	{"username": "Mewsick", "bot": true, "token": "YOUR BOTS NEW TOKEN", "avatar": "338f4d9d97056ae22c4a3feab5f0da07", "discriminator": "1550", "id": "132254000253894656"}

Keep your bots Token safe. You have now succesfully created a bot!
You can now login with your Token.


.. _Curl's website: https://curl.haxx.se/download.html
.. _`Discord API Website`: https://discordapp.com/developers/applications/me

Installation
------------

Installation via Gradle and Maven are super recommended and is the easiest way to install Discord4J as a libary for your project.
Gradle and Maven will install Discord4J and all Discord4J's dependencies. Gradle and Maven downloads from the same host, same directory but isnt identical software wise.
In addition, Gradle and Maven can build the project for you.

In Gradle you have a build.gradle file that gives information about what dependencies you need and how the file should be build etc.

In Maven you have a pom.xml file that gives the information. Scroll down and see the difference.

Gradle and maven are preset with Maven repository host. You can add more host by getting the host url.

Let's take the url where Discord4J is hosted: https://jitpack.io, and let's give it the name: jitpack.io.

Now we have the host, we need the project to be downloaded by Gradle and Maven. We need the dependency's groupId, artifactId, and a version.

Let's take Discord4J's  information: com.github.austinv11, Discord4j, and version 2.4.4 .

When we give that information to Gradle/Maven it tells them to download dependencies from the directory and puts them in your Window's User folder. ex: C:/Users/FjongyBoy/.gradle/.
This is amazing. If you're working on more than one bot, theyre using the same Dependency, which mean two different dependency jars isn't on your disk. This saves space.

For more information about Maven: `Maven Getting Started Guide`_

For more information about Gradle: `Gradle Getting Started Guide`_

Install via Maven:


Replace @VERSION@ with the version number.
It is highly recommended to use the latest version.
Check the `Discord API Chat`_ for the latest version.

.. code-block:: Maven

	...
	<repositories>
	  ...
	  <repository>
		<id>jitpack.io</id>
		<url>https://jitpack.io</url>
	  </repository>
	</repositories>
	...
	<dependencies>
	  ...
	  <dependency>
		<groupId>com.github.austinv11</groupId>
		<artifactId>Discord4j</artifactId>
		<version>@VERSION@</version>
	   <!-- <classifier>shaded</classifier> <!-- Include this line if you want a shaded jar (all the Discord4J dependencies bundled into one jar)-->
	  </dependency>
	</dependencies>
	...





Install via Gradle:


Replace @VERSION@ with the version number.
It is highly recommended to use the latest version.
Check the `Discord API Chat`_ for the latest version.

IMPORTANT: Gradle comes with mavenCentral as default in the repositories thingy.. Change that to jcenter()!


.. code-block:: Gradle

	...
	repositories {
	  ...
	  maven {
		url  "https://jitpack.io"
	  }
	}
	...
	dependencies {
	  ...
	  compile "com.github.austinv11:Discord4j:@VERSION@"
	  //compile "com.github.austinv11:Discord4j:@VERSION@:shaded" //Use this line instead of the one above it if you want a shaded jar (all the Discord4J dependencies bundled into one jar)
	}
	...


Logging Error?
------------

When running the project, you'll see that you need a file, in console. You need a Slf4 logger.
This means that you can specify what logger you want to use.

If you have now idea what logger to use, and you really dont care. You can use the Slf4j-simple logger.


Gradle and Maven are preset with the Maven repository which means that you dont need to specify a url.

Get it via Gradle or Maven:


Maven:

.. code-block:: Maven

	<dependencies>
	  ...
	  <dependency>
		<groupId>org.slf4j</groupId>
		<artifactId>slf4j-simple</artifactId>
		<version>1.7.9</version>
	  </dependency>
	</dependencies>
	...

Gradle:

.. code-block:: Gradle

	...
	dependencies {
	  ...
	  compile "org.slf4j:slf4j-simple:1.7.9"
	}
	...

.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1
.. _Maven Getting Started Guide: https://maven.apache.org/guides/getting-started/
.. _Gradle Getting Started Guide: http://gradle.org/getting-started-gradle-java/
