# FreedyMinigameMaker 이벤트 명령

#### 이벤트 번들


**이벤트 번들은 어떤 상황에서 명령들을 실행합니다**


```yaml
blockBreakCmd:
- fut {player} sendMsg private no!
- fut {player} cancelEvent
```

`preJoinCmd`
플레이어가 미니게임에 참여하기 직전에 실행됩니다.

`joinCmd`
플레이어가 미니게임에 참여했을 때 실행됩니다.

`preQuitCmd`
플레이어가 미니게임을 퇴장하기 직전에 실행됩니다.

`quitCmd`
플레이어가 미니게임을 퇴장했을 때 실행됩니다.

`conStartCmd`
미니게임이 시작됬을 때 실행됩니다.

`preConEndCmd`
미니게임이 종료되기 직전에 실행됩니다.

`conEndCmd`
미니게임이 종료되고 실행됩니다.

`interactCmd` `{actionName} {action} {itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 엔티티를 제외한 무언가를 클릭하거나 상호작용했을 때 실행됩니다.

`interactEntityCmd` `{entityName} {entityType} {itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 엔티티를 클릭했을 때 실행됩니다.

`moveCmd:` `{fromBlockType} {fromBlockX} {fromBlockY} {fromBlockZ} {fromBlockFace} {fromBlockWorld} {toBlockType} {toBlockX} {toBlockY} {toBlockZ} {toBlockFace} {toBlockWorld}`
미니게임에 참여 중인 플레이어가 블럭 단위로 한 칸 움직였을 때 실행됩니다.

`blockBreakCmd` `{blockType} {blockX} {blockY} {blockZ} {blockFace}`
미니게임에 참여 중인 플레이어가 블럭을 부술 때 실행됩니다.

`blockPlaceCmd` `{blockType} {blockX} {blockY} {blockZ} {blockFace}`
미니게임에 참여 중인 플레이어가 블럭을 설치할 때 실행됩니다.

`blockDamageCmd` `{blockType} {blockX} {blockY} {blockZ} {blockFace}`
미니게임에 참여 중인 플레이어가 블럭을 때릴 때 실행됩니다.

`preDeathCmd` `{killerType} {killerName}`
미니게임에 참여 중인 플레이어가 죽기 직전에 실행됩니다.

`deathCmd` `{killer}`
미니게임에 참여 중인 플레이어가 죽고 실행됩니다.

`damagedCmd` `{entityName} {entityType} {itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 어떤 엔티티에게 데미지를 줄 때 실행됩니다.

`damageCmd` `{cause}`
미니게임에 참여 중인 플레이어가 데미지를 입었을 때 실행됩니다.

`projectileCmd` `{cause}` `{damage}` `{projectileType}` `{projectileName}` `{projectileUuid}` `{entityName} {entityType}`
미니게임에 참여 중인 플레이어가 발사체로부터 데미지를 입었을 때 실행됩니다.

`dropCmd` `{itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 아이템을 떨굴 때 실행됩니다.

`pickupCmd` `{itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 아이템을 주울 때 실행됩니다.

`chatCmd` `{format} {chat}`
미니게임에 참여 중인 플레이어가 채팅을 칠 때 실행됩니다.

`commandCmd` `{command} {args}`
미니게임에 참여 중인 플레이어가 명령어를 칠 때 실행됩니다.

`worldChangeCmd` `{fromWorld}` `{toWorld}`
미니게임에 참여 중인 플레이어가 월드를 이동할 때 실행됩니다.

`vehicleDamageCmd` `{vehicleName}` `{vehicleType}`
미니게임에 참여 중인 플레이어가 보트나 카트에게 대미지를 줄 때 실행됩니다.

`vehicleExitCmd` `{vehicleName}` `{vehicleType}`
미니게임에 참여 중인 플레이어가 보트나 카트를 타고 있다가 내릴 때 실행됩니다.

`vehicleCollisionCmd` `{vehicleName}` `{vehicleType}`
미니게임에 참여 중인 플레이어가 타고 있는 보트나 카트가 엔티티와 충돌할 때 실행됩니다.

`명령번들이름Cmd` `{커스텀함수}`
`/fut <미니게임플레이어> do 명령번들이름 커스텀함수1, 값1, 커스텀함수2, 값2 ...`
do 실행 명령을 통해서 실행됩니다.

`keeped명령번들이름Cmd` `{커스텀함수}`
`/fut <미니게임플레이어> do keeped명령번들이름 커스텀함수1, 값1, 커스텀함수2, 값2 ...`
do 실행 명령을 통해서 실행됩니다 keeped번들은 데이타 함수가 대체되지 않습니다. 그래서 무의미한 /fut <player> if true == true 구문을 앞에 붙여서 데이타 함수를 대체해야 합니다.
이러한 keeped번들의 장점은 while 구문에서 데이타 함수를 매주기마다 새롭게 불러올 수 있고, 또 allPlayer 데이타 함수의 반복 구문에서 새롭게 데이타를 불러올 수 있습니다.

`메뉴이름ClickCmd` `{slot}`
어떤 메뉴이름의 GUI메뉴를 클릭했을 때 그 클릭한 위치 {slot}으로 명령번들을 실행합니다.
