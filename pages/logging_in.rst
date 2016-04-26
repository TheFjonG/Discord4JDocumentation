Logging In
===============

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ on the Discord4J channel.

Tutorial
------------

Alright let's start with a clean Java app.

.. code-block:: java

	public class TestBot
	{
		public static void main(String[] args)
		{

		}
	}

Now you'll want to make a method that will return an `IDiscordClient`_ object. Extend your class with the getClient method & add a *throws Exception* to your main method's signature.

.. code-block:: java

	public class TestBot
	{
		public static void main(String[] args) throws Exception
		{

		}

		public static IDiscordClient getClient(String token) throws DiscordException
		{
			return new ClientBuilder().withToken(token).login();
		}
	}

This method will take a `bot token`_ as a parameter, and return an IDiscordClient. (The 'Getting Started' section outlines getting a token)

Now you want to make a *public static* variable in your class, that you'll set to getClient(*YOUR TOKEN*). Your class should look similar to this:

.. code-block:: java

	public class TestBot
	{
		public static IDiscordClient discordClient;

		public static void main(String[] args) throws Exception
		{
			if(args.length < 1)
				System.out.print("You need to specify a token before continuing");

			discordClient = getClient(args[0]);
		}

		public static IDiscordClient getClient(String token) throws DiscordException
		{
			return new ClientBuilder().withToken(token).login();
		}
	}

This will take an argument and pass it to the getClient method. When you run your jar, remember to put a token as an argument!

An alternative to the current approach is to just hardcode the your bot's token. Which you may find convenient for
testing.

Now you have successfully logged in to your *discordClient*!

Completed Example
------------

.. code-block:: java

	public class TestBot
	{
		public static IDiscordClient discordClient;

		public static void main(String[] args) throws Exception
		{
			if(args.length < 1)
				System.out.print("You need to specify a token before continuing");

			discordClient = getClient(args[0]);
		}

		public static IDiscordClient getClient(String token) throws DiscordException
		{
			return new ClientBuilder().withToken(token).login();
		}
	}

.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1
.. _bot token: https://discordapp.com/developers/docs/topics/oauth2
.. _IDiscordClient: https://github.com/austinv11/Discord4J/blob/master/src/main/java/sx/blah/discord/api/IDiscordClient.java
