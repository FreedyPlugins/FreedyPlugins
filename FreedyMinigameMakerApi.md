

## 개발자 API

## 디펜덴시
```xml
        <dependency>
            <groupId>Freedy</groupId>
            <artifactId>FreedyMinigameMaker</artifactId>
            <version>버전</version>
            <scope>system</scope>
        </dependency>
```


## 예시
```java
package freedy.learnspigot.events;

import freedy.freedyminigamemaker.FreedyMinigameMaker;
import freedy.freedyminigamemaker.MiniGame;
import freedy.freedyminigamemaker.MiniGames;
import freedy.learnspigot.LearnSpigot;
import org.bukkit.command.Command;
import org.bukkit.command.CommandExecutor;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;

public class ChatEvent implements CommandExecutor {

    LearnSpigot plugin;

    public ChatEvent(LearnSpigot plugin) {
        this.plugin = plugin;
    }


    public boolean onCommand(CommandSender sender, Command command, String label, String[] args) {
        if (args.length == 1) {
            if (sender instanceof Player) {
                Player player = (Player) sender;
                MiniGames miniGames = FreedyMinigameMaker.miniGames;
                if (miniGames.isJoined(player)) {
                    MiniGame miniGame = miniGames.getJoined(player);
                    for (Player p : miniGame.playerList) {
                        p.sendMessage("<" + p.getName() + "> " + args[0]);
                    }
                }
            }
        }

        return true;
    }
}
```
