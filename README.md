# DcBotHelper
This will help you to build your own Discord bot faster!
## Implement to your project
``TODO``
## Get started
When creating a bot at the [Discord Developer Portal](https://discord.com/developers), please don´t forget to toggle every privileged gateway intent on.

### Starting the bot
#### Prepared method
You can start your bot using this method:
```java 
Bot.startBot(YOUR_TOKEN_HERE); // Enter your token
```
#### Custom method
Or create your own method and add the EventHandler to the EventLiteners.
```java
JDA bot = JDABuilder.createDefault(YOUR_TOKEN_HERE) // Enter your token
    .setStatus(OnlineStatus.ONLINE) // optional
    .setActivity(Activity.playing("nothing")) //optional
    .setChunkingFilter(ChunkingFilter.ALL)
    .setMemberCachePolicy(MemberCachePolicy.ALL)
    .enableIntents(
        GatewayIntent.GUILD_MEMBERS,
        GatewayIntent.GUILD_PRESENCES,
        GatewayIntent.GUILD_VOICE_STATES,
        GatewayIntent.DIRECT_MESSAGE_TYPING,
        GatewayIntent.DIRECT_MESSAGES,
        GatewayIntent.MESSAGE_CONTENT,
        GatewayIntent.GUILD_INVITES
    )
    .addEventListeners(
        new EventHandler()
    )
    .build().awaitReady();
```
### Some Events
Here are some examples how to make some Events.
#### Create a slash command
Add `@OnCommand` with a `name` and `description` to a method, give the method a name and make it static and add `SlashCommandInteractionEvent event` as the parameter.
```java
@OnCommand(name = "example", description = "example command")
public static void example(SlashCommandInteractionEvent event) {
    event.reply("This is an example!").setEphemeral(true).queue();
}
```
This will automatecly create a slash command and run whenever the command is used.
#### Listen to buttons
Add `@OnButton` with an `id` to a method, give the method a name, make it static and add `ButtonInteractionEvent event` as the parameter.
```java
@OnButton(id = "exampleButton")
public static void exampleBtn(ButtonInteractionEvent event)
{
    event.reply("You clicked on a button!").setEphemeral(true).queue();
}
```
This will run whenever a button is clicked which has the same id.

*The id is made when creating the button: `Button b = Button.success(id, label);`*
#### Handle String Selections
Ass `@OnStringSelection` with an `id` to a method, give the method a name, make it static and add `StringSelectionEvent event` as the parameter.
```java
@OnStringSelection(id = "exampleStringSelection")
public static void exampleStringSelection(StringSelectionEvent event) {
    event.reply("A string selection was made!").setEphemeral(true).queue();
}
```
You can also specify an optional `option` to handle a specific string value.
```java
@OnStringSelection(id = "exampleStringSelection", option = "specificOption")
public static void exampleSpecificStringSelection(StringSelectionEvent event) {
    event.reply("A specific string option was selected!").setEphemeral(true).queue();
}
```
*The `option` parameter is optional. If provided, the method will be triggered only for that specific option.*
## MORE IS IN PROGRESS PLEASE WAIT.
