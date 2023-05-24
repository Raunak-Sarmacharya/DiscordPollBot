# DiscordPollBot
# Requirements
aiohttp==3.8.4
aiosignal==1.3.1
async-timeout==4.0.2
attrs==22.2.0
charset-normalizer==3.1.0
discord==2.2.2
discord.py==2.2.2
frozenlist==1.3.3
idna==3.4
multidict==6.0.4
python-dotenv==1.0.0
yarl==1.8.2


The Discord bot is created using the Client class from the discord module, with specified intents that enable message content and member-related events.

The on_message event handler is defined to handle messages received by the bot. It checks if a message starts with the command "!create_poll" and extracts the parameters for creating a poll, such as the name, question, options, and countdown.

The code validates the provided parameters to ensure they meet the required format. If any errors are detected, an error message is sent as a Discord embed.

If the parameters are valid, the bot sends a poll message as a Discord embed, displaying the poll's name, question, and options. It also adds reaction emojis corresponding to each option.

The sent message ID is stored in a global list to keep track of poll messages created by the bot.

A background task called update_countdown is defined using the tasks.loop decorator. This task calculates the remaining time in the countdown and edits the poll message accordingly. If the countdown expires, the task collects and calculates the poll results, sends a results message, and deletes the original poll message.

The on_raw_reaction_add event handler is defined to handle reactions added to poll messages. It checks if the reaction was added to a poll message sent by the bot and validates if the reaction emoji is allowed. Duplicate votes from the same user are removed.

The validate_params function is defined to validate the provided parameters for creating a poll and returns an error message if any issues are found.

Finally, the Discord bot is started by calling the run method on the Client object with the Discord token provided.

This code enables users to create and manage polls within a Discord server using the bot's commands and reactions. It offers an interactive and engaging way to gather opinions and facilitate decision-making processes.
