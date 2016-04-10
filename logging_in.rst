Logging In
===============

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ in the Discord4J channel.

Tutorial
------------

.. code-block:: java
	
	public class TestBot
	{

		public static void main(String[] args) 
		{

		}

	}
	
Now you'll want to make a method that return an IDiscordClient Object. Extend your class with the getClient method. and add a throws Exception ending after your Main Method.

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

This Method will take a bot token as a parameter, and return an IDiscordClient.

Now you want to make a public static Variable in your class, that you'll set to getClient(*YOUR TOKEN*). Your class should look like this:

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

This will take an argument and pass it to the getClient method. When you run your jar, remember to put a token as an argument

You can also hardcode the bot to use your token.

Now you have succesfully logged in to your discordClient.

Full Example
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
