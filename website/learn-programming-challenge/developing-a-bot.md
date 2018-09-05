---
layout: doc_page
title: Developing a Bot
breadcrumb: Learn
toc: false
description: Get help debugging your bot, and hints about best practices for writing a bot.
sort_key: 3
---

<div class="doc-section" markdown="1">

#### Best Practices

##### Logging
stdout and stdin are used to communicate with the game engine. Any use of functions like `System.out.println`, `print()`, or `std::cout` will cause engine errors. Instead, print debugging information to a log file.

The starter kits have some functionality to write to a log file, and should include a simple log statement for your reference.

When your bot times out or errors on the game servers, we save and display a log file with debugging information. You will be sent an email with this log, or you can visit your profile to find the logs from your recent games.

##### Test new vs. old before upload
Before submitting a new bot, we recommend running some games against the previous version of your bot. You can play your bot against older versions using the CLI, or on our website here.

</div>
<div class="doc-section" markdown="1">

#### Debugging

##### Compilation Failures
You will get an email notifying you if your bot fails to compile on the game servers. The most common causes of compilation failures are:
* **Compilation errors in your code:** Make sure that you can compile your bot locally before submitting it to our game servers. A typo can make a big difference!
* **Infrastructure issues:** You can reach out to the Halite Team to add first class support for your bot. To read more about customizing a bot, check out our guide here.
* **Incorrect bot archive structure:** Your file structure should adhere to the following format:
  * You should have a `MyBot.{extension for language}` in the root folder of your zip archive.
  * If you are building on top of a starter kit provided by us, make sure to include the hlt folder.


##### Timeout Failures
Your bot will be killed if it exceeds the following time limits during game execution. You will receive a timeout email with a link to the log. You can also access these logs on your user profile. We will disable bots that time out excessively to ensure fair and productive games for everyone.
* **Install Time:** Prior to game start, you have `10 minutes` to install any dependencies.
* **Initialization Time:** Prior to the first turn, you have `1 minute` to compute any game specific data and return your bot’s name.
* **Per Turn Time:** Each player has at `max 2 seconds` per turn to respond with a command to the engine. If your bot exceeds this time limit, your bot is killed and loses the match.


To prevent your bot from timing out, you should optimize your code wherever possible. You might implement a timer to ensure that your bot returns commands in time to prevent losing the match.

When debugging timeout issues, it can be helpful to disable game engine timeouts. To do so, append the -t flag when running a game:
`TODO CLI example`

##### In Game Failures
Your bot could be crashing because of errors during game execution.
* **Incorrect commands:** The most common reason for incorrect commands is using the inbuilt functions incorrectly, or writing new functions that emit commands that the game engine cannot parse. Check your formatting, and make sure that your raw command strings are valid engine commands.
* **Out of memory:** Bots have a specific memory limit. If your code exceeds this limit, your bot is killed. See our more detailed page on the game environment.

##### Reproducing Maps
You can replay games with the exact same map to debug or tweak bot behavior. To do so, specify a map seed with the -s flag when running a game:
TODO

##### Debugging with an IDE
TODO


</div>

<div class="build-a-bot text-center">
  <a href="#" class="btn btn-primary">Build a bot</a>
</div>