User
===============

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ in the Discord4J channel.

Getting a user by ID
-------------------------

You can type out the user with the @mention syntax (i.e. @Austin) an add a backslash in front (like this: \\@Austin). Sending the message should get you the user id in the form "<@USER_ID>". NOTE: This will still mention the user!


Now we want to use it in our ultra amazing bot.

.. code-block:: java

    public IUser getUserForID(IDiscordClient client, String id)
    {
        return client.getUserByID(id);
    }

That was quite easy.

Get the voice channel our bot is connected to (if present)
-------------------------

.. code-block:: java

    public Optional<IVoiceChannel> getVoiceChannel(IDiscordClient client, String userID)
    {
        return client.getUserByID(userID).getVoiceChannel();
    }

Sending a Private Message
-------------------------

.. code-block:: java

    public void sendPrivateMessage(IDiscordClient client, String userID) throws DiscordException, HTTP429Exception, MissingPermissionsException
    {
        IPrivateChannel channel = client.getOrCreatePMChannel(client.getUserByID(userID));
        channel.sendMessage("Hello User");
    }

There's an overload of information at our `Java Docs`_. This is just a little piece of the awesomeness

.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1
.. _Java Docs: https://austinv11.github.io/Discord4J/docs.html
