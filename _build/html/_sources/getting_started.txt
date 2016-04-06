Getting Started
===============

Requirements
------------

Discord4J requires you to have a registered Account or a bot account.
You can `register an account here`_.

It is highly recommended that you make a bot account for your application.

.. _register an account here: https://discordapp.com/register

Making a bot account
--------------------

* Install Curl from `Curl's website`_

* You will need 2 accounts. 1 Main Account & 1 Bot Account.

"YOUR.." Is your Main account's information.
"YOUR BOTS..." Is your Bot's Information.

Now you want to make an application.
Run this via CMD or Terminal:

.. code-block:: Bash

	curl -H 'Authorization: [YOUR TOKEN]' \
	-H "Content-Type: application/json" \
	-X POST -d '{"name": "[YOUR BOTS USERS TOKEN]"}' \
	https://discordapp.com/api/oauth2/applications

You should get a response like this:

.. code-block:: Bash

	{"secret": "XXX", "redirect_uris": [], "description": "", "name": "YOUR BOTS NAME HERE", "id": "YYY", "icon": null}
	
Keep the 'secret' and the 'ID' safe.
You have now succesfully created an application!

Now you want to make the bot itself.
Run this via CMD or Terminal:

.. code-block:: Bash

	curl -H 'Authorization: [YOUR TOKEN]' \
    -H "Content-Type: application/json" \
    -X POST -d '{"token": "[YOUR BOTS USERS TOKEN]"}' \
    https://discordapp.com/api/oauth2/applications/[Your Application's ID]/bot

You should get a response like this:

.. code-block:: Bash
	
	{"username": "Mewsick", "bot": true, "token": "YOUR BOTS NEW TOKEN", "avatar": "338f4d9d97056ae22c4a3feab5f0da07", "discriminator": "1550", "id": "132254000253894656"}
	
Keep your bots Token safe. You have no succesfully created a bot!
You can now login with your Token.


.. _Curl's website: https://curl.haxx.se/download.html



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
