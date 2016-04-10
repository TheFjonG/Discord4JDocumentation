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
If youre going with Discord's bot maker, then make an Application, then add the bot account afterwards. ;)

Otherwise, you can follow this CURL tutorial:

* Install Curl from `Curl's website`_

There are 2 ways of getting a bot account.

* The 1. way first you'll need 2 account registred at Discord. Your main and your bot account.
* The 2. way you'll only need 1 account registered at Discord. Your main account only

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
	
Keep your bots Token safe. You have no succesfully created a bot!
You can now login with your Token.


.. _Curl's website: https://curl.haxx.se/download.html
.. _`Discord API Website`: https://discordapp.com/developers/applications/me

Installation
------------

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


.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1
