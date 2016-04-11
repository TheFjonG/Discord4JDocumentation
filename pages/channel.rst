Channel
===============

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ in the Discord4J channel.

Getting a channel by ID
-------------------------

First of all you might be wondering how to get the id from a channel. Do following:


.. image:: ../images/gettingidofchannel.png

Afterwards, put the link in notepad or something. Then copy the id out of it, like I do here:

.. image:: ../images/gettingidofchannel1.png


Now we want to use it in our ultra amazing bot. 

.. code-block:: java
	
    public IChannel changeBotAvatar(IDiscordClient client, String id)
    {
        return client.getChannelByID(id);
    }

That was quite easy.

Let's make something more out of that.

Creating an invite
------------------

1 parameter in create invite is how long the invite should last. 2. is how many users can use the invite. 3. is whether the invite is temporary. 4. is if the invite should be human-readable. 

.. code-block:: java
	

    public IInvite createInvite(IDiscordClient client, String id) throws MissingPermissionsException, HTTP429Exception, DiscordException
    {
        return client.getChannelByID(id).createInvite(0, 0, false, false);
    }

Now you have a invite for a channel. What about accepting one from a channel?

Accepting an invite
-------------------

.. code-block:: java

    public InviteResponse acceptInvite(IDiscordClient client, String invite) throws DiscordException, HTTP429Exception
    {
        return client.getInviteForCode(invite).accept();
    }

Let's amagine you just made a invite, but you realize you did something stupid. Let's delete it :D

Deleting an invite
-------------------

.. code-block:: java

    public void deleteInvite(IDiscordClient client, String invite) throws HTTP429Exception, DiscordException
    {
        client.getInviteForCode(invite).delete();
    }

Now you know exactly how to manage invites. 

Getting Messages in a channel
------------------------------

.. code-block:: java

	public MessageList getMessages(IDiscordClient client, String ChannelID)
    {
        return client.getChannelByID(ChannelID).getMessages();
    }

Toggling Typing Status
-----------------------

.. code-block:: java 

	public void toggleTypingStatus(IDiscordClient client, String ChannelID)
    {
        client.getChannelByID(ChannelID).toggleTypingStatus();
    }

Changing Channel Name, Position & Topic
----------------------------------------

.. code-block:: java

    public void changeChannel(IDiscordClient client, String ChannelID)
    {
        client.getChannelByID(ChannelID).changeName("Bot chat");
        client.getChannelByID(ChannelID).changePosition(0);
        client.getChannelByID(ChannelID).changeTopic("Bot chat, only for Awesome bots...");
    }


Sending files and messages
---------------------------

.. code-block:: java

    public void SendFileAndMessage(IDiscordClient client, String ChannelID)
    {
        client.getChannelByID(ChannelID).sendFile(new File("filetosend"));
        client.getChannelByID(ChannelID).sendMessage("Heyo Everyone.. wut");
    }

.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1

