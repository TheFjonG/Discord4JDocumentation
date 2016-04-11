User Settings
===============

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ in the Discord4J channel.

Updating Presence / Game information
------------

.. code-block:: java
	
    public void updateBotPresence(IDiscordClient client)
    {
        client.updatePresence(false, Optional.of("Bot things :3"));
    }
	
Changing Username
------------

.. code-block:: java
	
    public void changeBotUsername(IDiscordClient client) throws DiscordException, HTTP429Exception
    {
        client.changeUsername("Butt bot");
    }

Changing Avatar
------------

.. code-block:: java

    public void changeBotAvatar(IDiscordClient client)
    {
        client.changeAvatar(Image.forFile(new File("BotAvatar.png")));
        client.changeAvatar(Image.forUrl("jpg", "Random.org/avatar.jpg"));
        client.changeAvatar(Image.forData("jpg", **Byte Array**));
        client.changeAvatar(Image.forUser(client.getUserByID("UserID of the person you want to get the image from"));
        client.changeAvatar(Image.forStream("png", **InputStreamObject**));
    }

.. _Discord API Chat: https://discord.gg/0SBTUU1wZTX5pYo1
