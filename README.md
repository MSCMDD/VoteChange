## 关于汉化组

汉化者为：
AoMe奥美互助公社——Ленинград
AoMe Mutual Aid Commune

![AoMe奥美互助公社](https://mscmdd.github.io/www/index.files/aome.svg)

# 关于VoteChange汉化版

克隆自[VoteChange (github.com)](https://github.com/nicasnes/VoteChange/tree/master/VoteChange/src/main)是其汉化分支。

# 关于VoteChange

一个 Minecraft 插件，允许基于多数的投票来执行命令。

# 安装

下载.jar文件并将其放在服务器的插件文件夹中。

# 配置

服务器管理员通过 config.yml 文件对插件的实现有一定程度的自由。安装插件并启动服务器一次后，将生成一个config.yml文件。要编辑字段，请删除预生成的数据
，然后输入所需的值。下面列出了具体的配置选项。

**投票持续时间-秒** 
默认投票持续时间为 20 秒。此值应为正数实数。

**法定多数** 
默认多数要求为 0.666。此值具有包容性，这意味着确切的 0.666 多数将产生成功的投票。此值应为 0.0 和 1.0 之间的小数。

**最低玩家** 
默认最小玩家计数为 3。当服务器的玩家计数小于此数字时，仅允许列入白名单的命令。

**空投票消息** 
当用户尝试使用不带参数的 callvote 命令时，将向用户发送此消息。

**单排队消息** 
当用户尝试向队列添加第二个投票时，将向用户发送此消息。

**仅一票消息** 
当用户尝试在已发生投票时调用投票时，将向用户发送此消息。

**命令列入黑名单的消息** 
当用户尝试对列入黑名单的命令进行投票时，将向用户发送此消息。

**未达到上限消息** 
当没有足够的在线玩家对他们尝试的命令进行投票时，此消息将发送给用户。

**仅限玩家的消息** 
当非玩家尝试调用投票（即控制台）时，将发送此消息。

**队列空消息** 
当队列为空时，此消息将发送给使用 viewqueue 或 callqueue 命令的用户。

**队列清除消息** 
此消息将发送给执行 clearqueue 命令的用户。

**列入黑名单的命令** 
这必须作为列表输入，每个参数都是包含在单引号或双引号中的字符串。默认情况下，唯一列入黑名单的命令是 op。命令可以是通用的，例如“时间”，它将把所有命令列入黑名单
涉及时间的命令，或特定的命令，例如不允许此特定命令的“时间设置夜晚”。例如，用户仍然可以执行命令“时间设置日”。此列表中的命令永远不会
投票通过。

**列入白名单的命令** 
这必须作为列表输入，每个参数都是包含在单引号或双引号中的字符串。默认情况下列入白名单的命令包括时间和天气。同样，命令可以是特定的或通用的。这
即使未达到最低玩家要求，也允许此白名单上的命令进行投票。

# 命令

**呼叫投票**

###### votechange.cv

此命令可以接受任何字符串作为参数，但它应该是 Minecraft 服务器中的工作命令。如果投票获得 2/3 多数的*是*票，则用户将执行该命令。当前投票期持续十秒。用户目前无法投票将自己设置为服务器运营商。

用法示例：  
*/callvote gamemode creative myUserName*  
*/cv time set day*  
*/callvote weather clear*  

**投票**
####### votechange.v
此命令允许用户在当前调用的投票中投票。投票命令的参数只能是*yes*或*no*。

用法示例：  
*/vote yes*  
*/v no* 
*/vote yes but only the first argument is considered*仍将投赞成票。 
*/vote no yes*将投反对票，因为只考虑第一个参数。  

**清除队列**

###### votechange.cq

此命令允许用户清除即将进行的投票的队列。默认权限要求仅为服务器操作员。

用法示例：
*/clearqueue*
*/cq*

**查看队列**
####### votechange.vq
此命令允许用户查看队列的内容。

用法示例：
*/viewqueue*
*/vq*



# 以下为原文

# VoteChange

A Minecraft plugin allowing for majority-based voting to execute commands.

# Installation

Download the .jar file and place it in the plugins folder of your server. 

# Configuration

Server administrators have a degree of freedom with the plugin's implementation through the config.yml file. After installing the plugin and launching the server once, a config.yml file will be generated. To edit a field, delete the pregenerated data
and  enter the desired value. Specific configuration options are listed below.

**vote-duration-seconds**  
The default vote duration is 20 seconds. This value should be a positive, real number.

**required-majority**  
The default majority requirement is 0.666. This value is inclusive, meaning that an exact 0.666 majority will yield a successful vote. This value should be a decimal between 0.0 and 1.0. 

**minimum-players**  
The default minimum player count is 3. When the player count of the server is less than this number, only whitelisted commands will be allowed.

**empty-vote-message**  
This message is sent to the user when they attempt to use the callvote command with no arguments.

**one-queued-message**  
This message is sent to the user when they attempt to add a second vote to the queue.

**only-one-vote-message**  
This message is sent to the user when they attempt to call a vote while there is already a vote occurring.

**command-blacklisted-message**  
This message is sent to the user when they attempt to call a vote on a blacklisted command.

**cap-not-reached-message**  
This message is sent to the user when there are not enough players online to call a vote on the command they attempted.

**players-only-message**  
This message is sent when a non-player attempts to call a vote (i.e, console).

**queue-empty-message**  
This message is sent to a user who uses the viewqueue or callqueue command when a queue is empty.

**queue-cleared-message**  
This message is sent to a user who executes the clearqueue command.

**blacklisted-commands**  
This must be entered as a list with each argument being a String contained in single or double quotes. The only command blacklisted by default is op. The commands can be general such as "time" which would blacklist all
commands involving time, or specific such as "time set night" which would disallow this specific command. Users would still be able to execute command "time set day", for example. Commands on this list will never be 
voted on.

**whitelisted-commands**  
This must be entered as a list with each argument being a String contained in single or double quotes. Commands whitelisted by default include time and weather. Once again, the commands can be specific or general. The
commands on this whitelist will be allowed for voting even if the minimum-players requirement is not reached.

# Commands

**callvote**

###### votechange.cv

This command can take any String as a parameter, but it should be a working command in your Minecraft server. If the vote receives a 2/3 majority of *yes* votes, the user will execute the command. The current voting period lasts ten seconds. Users cannot vote to set themselves a server operator at the present moment.

Example usage:   
*/callvote gamemode creative myUserName*  
*/cv time set day*  
*/callvote weather clear*  

**vote**

###### votechange.v

This command allows users to vote in the current vote being called. Arguments of the vote command can only be *yes* or *no*. 

Example usage:   
*/vote yes*  
*/v no*  
*/vote yes but only the first argument is considered* will still vote yes.  
*/vote no yes* will vote no, as only the first argument is considered.   

**clearqueue**

###### votechange.cq

This command allows the user to clear the queue of upcoming votes. Default permission requirement is server operator only.

Example usage:
*/clearqueue*
*/cq*

**viewqueue**

###### votechange.vq

This command allows the user to view the contents of the queue.

Example usage:
*/viewqueue*
*/vq*
