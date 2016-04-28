Audio
=======

If you have any problems with this guide, please contact @Thefjong in `Discord API Chat`_ in the Discord4J channel.

Grabbing a Channel
--------------------------

.. code-block:: java

    public AudioChannel getAudioChannel(IDiscordClient client, String id) throws DiscordException
    {
        return client.getVoiceChannelByID(id).getAudioChannel();
    }

Playing Audio Example
--------------------------

.. code-block:: java

    public void playFile(AudioChannel channel, String path) throws Exception
    {
        if (channel == null)
           throw new NullPointerException("Argument: 'channel'");

        // Let's make sure our bot is
        // actually there..
        channel.join();

        File _rawFile = new java.io.File(path);

        // :< | Handle how ever you see fit
        if (_rawFile == null)
           return;

        channel.queueFile(_rawFile);
        // You should hear the content
        // of that file now! :>
    }

General Media Control
--------------------------

.. code-block:: java

   public void example(AudioChannel channel)
   {
       // Interupts our bot's audio stream. It will
       // continue where it left off.
       channel.pause();
       // ^ This guy's partner
       channel.isPaused();

       // Resumes the bot's audio stream. Operates
       // well with the #pause() function
       channel.resume();

       // Updates the volume at which this bot
       // plays audio. This can go pretty darn
       // high, so avoid killing anyone's ears.
       channel.setVolume(4);
       channel.setVolume(1000); // <-- Evil

       // Jumps over the current playing file.
       // Like it was never even there!
       channel.skip();
   }
