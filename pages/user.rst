Channel
===============

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ in the Discord4J channel.

Getting user presence / game playing
-------------------------

.. code-block:: java
	
    public Presences SendFileAndMessage(IDiscordClient client, String userID)
    {
        client.getUserByID(userID).getPresence();
    }

Getting voice channel the user is connected to(if one)
-------------------------

.. code-block:: java
    
    public Optional<IVoiceChannel> getVoiceChannel(IDiscordClient client, String userID)
    {
        return client.getUserByID(userID).getVoiceChannel();
    }

Send a private message to user
-------------------------

.. code-block:: java
    
    public void SendPrivateMessage(IDiscordClient client, String userID) throws DiscordException, HTTP429Exception, MissingPermissionsException
    {
        IPrivateChannel channel = client.getOrCreatePMChannel(client.getUserByID(userID));
        channel.sendMessage("Hello User");
    }

There's lots of methods more... These are just some examples. see `Javadocs`_ for more. 

.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1
.. _JavaDocs: http://austinv11.github.io/Discord4J/docs.html
