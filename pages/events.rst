Events
===============

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ in the Discord4J channel.

See all Events here: `JavaDocs`_

Ready Event
------------

First you want to register a listener via your IDiscordClient variable. You can do so by the getDispatcher() method in IDiscordClient, and then registerListener(IListener).
You can either make an EventHandler that listens so all events that your class have an @EventSubscriber annotation over it, and make a file for each Event that you listens to.

See following code:

.. code-block:: java

	public static void main(String[] args) throws Exception
	{
		if(args.length < 1)
			System.out.print("You need to specify a token before continuing");

		discordClient = getClient(args[0]);

		discordClient.getDispatcher().registerListener(new EventHandler());
		discordClient.getDispatcher().registerListener(new ReadyEventListener());
	}

The line that has (new EventHandler()) registers a listener that works by making methods that has an @EventSubscriber annotation.

The line that has (new ReadyEventListener()) registers a listeners that implements IListener. This file will only react when one specific event is dispatched.

The EventHandler class:

.. code-block:: java

	public class EventHandler
	{
		@EventSubscriber
		public void onReadyEvent(ReadyEvent event)
		{
			System.out.println("The bot is now ready");
			doSomething();
		}

		@EventSubscriber
		public void onMessageEvent(MessageReceivedEvent event)
		{
			System.out.println(event.getMessage().getAuthor().getName() + ": " + event.getMessage().getContent());
		}
	}

The ReadyEventListener class:

.. code-block:: java

	public class ReadyEventListener implements IListener<ReadyEvent>
	{
		public void handle(ReadyEvent event)
		{
			System.out.println("The bot is now ready");
			doSomething();
		}
	}


The EventHandler class listens on 2 events. Both ReadyEvent and MessageReceivedEvent.
The class will print "The Bot is now ready" in the console when the ReadyEvent is dispatched.
The class will also print the a message with a name when the bot has received a message.

The ReadyEventListener only listens on ReadyEvent and will not be called when MessageReceivedEvent has been dispatched.

ReadyEvent is probably the most useful Events that Discord4J has, because you cant really do anything Discord wise without the bot being ready.


Full Example
------------


.. code-block:: java

	public static void main(String[] args) throws Exception
	{
		if(args.length < 1)
			System.out.print("You need to specify a token before continuing");

		discordClient = getClient(args[0]);

		discordClient.getDispatcher().registerListener(new EventHandler());
		discordClient.getDispatcher().registerListener(new ReadyEventListener());
	}

.. code-block:: java

	public class EventHandler
	{
		@EventSubscriber
		public void onReadyEvent(ReadyEvent event)
		{
			System.out.println("The bot is now ready");
			doSomething();
		}

		@EventSubscriber
		public void onMessageEvent(MessageReceivedEvent event)
		{
			System.out.println(event.getMessage().getAuthor().getName() + ": " + event.getMessage().getContent());
		}
	}

.. code-block:: java

	public class ReadyEventListener implements IListener<ReadyEvent>
	{
		public void handle(ReadyEvent event)
		{
			System.out.println("The bot is now ready");
			doSomething();
		}
	}

.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1
.. _JavaDocs: http://austinv11.github.io/Discord4J/docs.html
