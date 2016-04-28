Nifty Use Case Examples
====================

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ on the Discord4J channel.


Command System
-----------------------

Commands are an extremely common task handled by bots. One way to relieve the
amount of effort put into every command is to develop a small system to emit events
whenever one is executed.

Let's start by creating our listener to process messages, and search for commands.

.. code-block:: java

     public class CommandListener
     {

         // This is the executor that we'll look for
         final static String KEY = "!";

         public CommandListener(IDiscordClient client)
         {
             client.getDispatcher().registerListener(this);
         }

         @EventSubscriber
         public void watchForCommands(MessageReceivedEvent event)
         {
             try
             {

                 IMessage _message = event.getMessage();
                 String _content = _message.getContent();

                 if (!_content.startsWith(KEY))
                    return;

                 String _command = _content.toLowerCase();
                 String[] _args = null;

                 if (_content.contains(" "))
                 {
                     _command = _command.split(" ")[0];
                     _args = _content.substring(_content.indexOf(' ') + 1).split(" ");
                 }

             }
             catch (Exception ex)
             {
                 // Handle how ever you please
             }
         }

     }


Alright we have that done. Let's walk through what we just did..
* Someone sends your everyday casual message on a channel the bot was invited to
* We listen for the event fired by Discord4J. How nice of them!
* We grab that message from the event (_message)
* We also store the content of our message as we'll be using it quite a bit (_content)
* We verify that we're actually handling a command, and not those memes your friends keep sending. (_content.startsWith())
* Now that we're positive we're dealing with a command lets create some variables...

   * _command: This will hold our actual command the user used. (!help messages | 'help' is the command in this case)
   * _args: This will hold the arguments the user provided while executing the command. Keep in mind that they may not have done so!

* Wait a second! We have that 'args' variable, but by default we assign it to a null value... That doesn't make any sense! :/
   - That's a fair point! So that means we'll have to grab those..
* Remove that first pesky space, and then split the rest up into an array to make dealing with these arguments worlds easier.
* Listen for an event that is fired whenever we do this. Oh wait... let's go make that!

.. code-block:: java

    private final IMessage message;
    private final String command;
    private final IUser by;
    private final String[] args;

    public CommandExecutionEvent(IMessage message, String command, IUser by, String[] args)
    {
        this.message = message;
        this.command = command;
        this.by = by;
        this.args = args;
    }

    public String[] getArgs()
    {
        return args;
    }

    public IMessage getMessage()
    {
        return message;
    }

    public boolean isCommand(String command)
    {
        return command.equalsIgnoreCase(command);
    }

    public IUser getBy()
    {
        return by;
    }

* Alrighty. Now that we have that lets jump back to that other class...

.. code-block:: java

             .....
                 if (_content.contains(" "))
                 {
                     _command = _command.split(" ")[0];
                     _args = _content.substring(_content.indexOf(' ') + 1).split(" ");
                 }

                 CommandExecutionEvent _event = new CommandExecutionEvent(_message, _command, _message.getAuthor(), _args);
                 getClient().getDispatcher().dispatch(_event);
             .....

* The first addition was the creation of our event object containing all of the data for this event
* Next we tell Discord4J to fire that event off to all of our listeners which will handle our event accordingly
* We're done! Just for fun I'll also show you a quick use-case scenario for this

.. code-block:: java

    .....
    @EventSubscriber
    public void handle(CommandExecutionEvent event)
    {
        if (event.isCommand("ping"))
            event.getMessage().reply("Pong!");
    }
    .....

Good luck! :>

.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1
