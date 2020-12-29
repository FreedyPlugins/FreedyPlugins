# FreedyMinigameMaker 명령 구성

## 조건 명령

조건 명령은 데이터를 확인하고 다른 명령을 실행합니다.



`/fut <플레이어> if <값1> == <값2> <실행될명령>`  
만약 값1과 값2가 같다면 명령어를 실행하는 명령 구문입니다.



`/fut <플레이어> if <값1> /= <값2> <실행될명령>` 
만약 값1과 값2가 같지 않다면 명령어를 실행하는 명령 구문입니다.



`/fut <플레이어> if <값1> < <값2> <실행될명령>` 
만약 값1이 값2보다 작다면 명령어를 실행하는 명령 구문입니다.



`/fut <플레이어> if <값1> > <값2> <실행될명령>` 
만약 값1이 값2보다 크다면 명령어를 실행하는 명령 구문입니다.



`/fut <플레이어> if <값1> <= <값2> <실행될명령>` 
만약 값1이 값2보다 작거나 같으면 명령어를 실행하는 명령 구문입니다.




`/fut <플레이어> if <값1> >= <값2> <실행될명령>` 
만약 값1이 값2보다 크거나 같으면 명령어를 실행하는 명령 구문입니다.


`/fut <플레이어> if <값1> == <값2> fut <플레이어> if <값3> == <값4> <실행될명령>`  
만약 값1과 값2가 같고 값3과 값4가 같다면 명령어를 실행하는 명령 구문입니다.
  


  

`/fut <플레이어> if <값1> == <값2> {do(<명령1> && <명령2>)}`  
만약 값1과 값2가 같다면 명령1과 명령2를 실행하는 구문입니다
  

  
`/fut <플레이어> if <값1> == <값2> {do(<명령1> && <명령2>)}{else(<명령1> && <명령2>)}`
만약 값1과 값2가 같다면 명령1과 명령2를 실행하고 값1과 값2가 같지 않다면 명령3과 명령4를 실행하는 구문입니다


> 알림! {do()}나 {else()} 구문에서 여러 명령을 실행하려면 명렁과 명령 사이에 ' && ' (공백과 공백 사이에 '&&'를 넣은 문자열)을 넣어주세요
>> 주의! {do()}나 {else()} 구문 속에 {add()}나 {data()} 같은 데이타 함수를 넣으면 안되요! fut <player> do player, <player> 실행 명령을 통해 데이타 함수를 사용하세요


## 바닐라 명령어 실행

미니게임 명령번들이나 이벤트 명령이나 반복 명령 번들 같은 미니게임 설정에 있는 명령어가 /tp 나 /say 같은 마인크래프트 기본 명령어라면, 바로 실행하지 말아주세요.

`/fut <player> execute say hello`

이렇게 해주셔야 작동합니다.

## 커맨드블럭 호환

커맨드블럭에 fut 명령을 입력할 때 @p같은 명령어가 잘 작동 되지 않습니다. @s, @p 등등, 중에서 오직 @p만 작동하는데, 커맨드블럭 반경 4 블럭에 있는 가장 가까운 플레이어 이름을 대체합니다.



## 미니게임 대기 시작

미니게임은 플레이어가 한명이라도 있어야 실행됩니다. 플레이어가 아무도 없는 미니게임은 자동으로 비활성화됩니다. 그리고 미니게임의 최대 인원을 설정할 수 있고 미니게임의 시작 인원을 설정할 수 있고 시작 인원이 모두 모였을 때 몇 초후 시작 되게 할 수 있습니다. 

## 미니게임 이벤트

미니게임 이벤트는 말그대로 어떤 상황 또는 사건이 일어나면 이벤트 명령 번들이 실행됩니다. 플레이어가 블럭 단위로 움직였을 때는 아래와 같이 할 수 있습니다 이벤트에 관한 더 자세한 설명은 아래 페이지를 참고하세요.

```yaml
miniGames:
  테스트미니게임:
    maxPlayers: 20
    maxStartPlayers: 2
    waitForStartTime: 100 
    moveCmd:
    - fut {player} sendActionBar private {toBlockX} {toBlockY} {toBlockZ}
```

## 이벤트 취소

미니게임 이벤트가 더 이상 진행되는 것을 멈출 때 사용됩니다. 이 명령을 실행하면 이벤트가 취소 됩니다.

`/fut <player> cancelEvent`

fut <player> do ... 로 실행된 명령번들, 반복 명령 번들 {do()}, {else()}에서는 즉시 취소되고 다음 명령 까지 취소되지만, 미니게임 이벤트에서는 명령번들의 명령들이 모두 실행 된 후에 움직임 이벤트나 블럭 클릭 이벤트 같은 이벤트가 취소됩니다.

## 반복 명령

미니게임 시작 대기 중이거나 미니게임 플레이 중 일 때 반복 명령이 실행됩니다 반복 명령 이름을 wait으로 설정하면 미니게임이 시작 대기 중이거나 미니게임이 플레이 중일 때 실행됩니다. 이름이 wait이 아닌 반복 명령은 미니게임이 플레이 중일 때만 실행됩니다.


```yaml
repeats:
  timer:
    time: 20     #반복 명령 주기
    cmd:     #반복 명령 번들
    - fut {player} ...
    - fut {player} ...
```

```yaml
miniGames:
  테스트미니게임:
    maxPlayers: 20
    maxStartPlayers: 1
    waitForStartTime: 100 
    gameTime: 100
    repeatList:
    - wait
    - timer
    repeats:
      timer:
        time: 1
        cmd:
        - fut {player} if {isPlaying} == false fut {player} if {numeric({data(timer)})} == false fut {player} setData timer {constant(gameTime)}
        - fut {player} if {isPlaying} == false fut {player} if {numeric({data(timer)})} == true fut {player} do printBossBar
      wait:
        time: 20
        cmd:
        - fut {player} if {isPlaying} == false fut {player} if {numeric({data(wait)})} == false fut {player} setData wait 5
        - fut {player} if {isPlaying} == false fut {player} if {numeric({data(wait)})} == true fut {player} do printTime
    printTimeCmd:
    - fut {player} sendTitle game 10 50 10 {integer({data(wait)})}
    - fut {player} addData wait -1
    printBossBarCmd:
    - fut {player} sendBossBar game {game} {math(divide, {data(timer)}, {constant(gameTime)})} GREEN {game}
    - fut {player} addData timer -1
    - fut {player} if {data(timer)} < 0 fut {player} do stop
    stopCmd:
    - fut {player} sendMsg game 게임이 종료되었습니다
    - fut {player} shutDown
    quitCmd:
    - fut {player} sendBossBar private {game} 0 GREEN none
```

이 미니게임 설정을 예시로 들어보았습니다. 명령어로 설정하는 방법입니다.

/fmg set 테스트미니게임 setCmd repeatList 999 wait

/fmg set 테스트미니게임 msg repeats.time 20

/fmg set 테스트미니게임 setCmd repeats.cmd 0 fut {player} ...

## 미니게임 실행 명령어

`/fut <player> join`

`/fut <player> conLog <message>`
콘솔에 매세지를 출력합니다.

`/fut none setFile data.hello yes_hello`
data.yml 에 파일을 저장합니다.

`/fut none saveFile`
data.yml 을 세이브합니다.

`/fut <player> shutDown`
미니게임에서 플레이어를 모두 강제 퇴장 시킵니다.

`/fut <player> setData <customdata> <data>`
미니게임 데이타를 저장합니다

`/fut <player> addData <customdata> <amount>`
미니게임 데이타의 값에 더합니다.

`/fut <player> setPlayerData <customdata> <data>`
미니게임의 플레이어 데이타를 저장합니다.

`/fut <player> addPlayerData <customdata> <amount>`
미니게임의 플레이어 데이타의 값에 더합니다.

`/fut <player> execute <command>`
바닐라 명령어 실행


## 플레이어 및 엔티티 설정

`/fut <player> health private <체력>`
플레이어의 체력을 설정하는 명령어 입니다.

`/fut <player> food private <배고픔>`
플레이어의 배고픔을 설정하는 명령어 입니다.

`/fut <player> addPotion private SPEED 55555 1`
플레이어에게 신속 1을 무한으로 주는 명령어 입니다.

`/fut <player> removePotion private`
플레이어에게 적용된 포션을 모두 없애는 명령어 입니다.

`/fut <player> closeGui`
플레이어에게 띄워진 인벤토리 메뉴를 닫는 명령어 입니다.

`/fut <player> knockBack <x> <y> <z>`
플레이어에게 추진력을 주는 명령어 입니다.

`/fut <player> entityKnockBack <entityUuid> <x> <y> <z>`
엔티티에게 추진력을 주는 명령어 입니다.

`/fut <player> addKnockBack <amount> <yaw> <pitch>`
플레이어에게 어떤 방향으로 추진력을 주는 명령어 입니다.

`/fut <player> entityAddKnockBack <entityUuid> <amount> <yaw> <pitch`
엔티티에게 어떤 방향으로 추진력을 주는 명령어 입니다.

`/fut <player> setHelmet <customItem>`
저장되어 있는 아이템을 플레이어의 머리에 씌우는 명령어 입니다.

`/fut <player> setChestplate <customItem>`
저장되어 있는 아이템을 플레이어의 갑옷에 씌우는 명령어 입니다.

`/fut <player> setLeggings <customItem>`
저장되어 있는 아이템을 플레이어의 바지에 씌우는 명령어 입니다.

`/fut <player> setBoots <customItem>`
저장되어 있는 아이템을 플레이어의 신발에 씌우는 명령어 입니다.

`/fut <player> cursor <cursor>`
플레이어의 핫바 9칸 에서 커서를 설정하는 명령어 입니다.

`/fut <player> kill <entityUuid>`
엔티티를 단순이 죽이지 않고 삭제시키는 명령어 입니다.

`/fut <player> damage <entityUuid> <damage>`
엔티티에게 데미지를 주는 명령어 입니다.

`/fut <player> nearByEntities <x> <y> <z> <cmd>`
플레이어의 일정 범위 안에 있는 주변 엔티티로 <cmd>에 있는 명령을 실행합니다.
`{nearByEntitiyType}`, `{nearByEntitiyName}`, `{nearByEntitiyUUID}`, `{nearByEntitiyDistance}`

`/fut <player> entityNearByEntities <entityUuid> <x> <y> <z> <cmd>`
어떤 엔티티의 일정 범위 안에 있는 주변 엔티티로 <cmd>에 있는 명령을 실행합니다.
`{entityNearByEntitiyType}`, `{entityNearByEntitiyName}`, `{entityNearByEntitiyUUID}`, `{entityNearByEntitiyDistance}`

`/fut none ride <entityUuid> <passengerUuid>`
엔티티가 엔티티를 탑승합니다.

`/fut <player> removeRide`
탑승해 있는 엔티티에서 내립니다.

`/fut <player> repairItem`
플레이어가 들고 있는 아이템의 내구도를 수리합니다.





## 키트

키트는 config 설정에서 인벤토리를 저장하고 불러오는 기능을 합니다.

`/fmg set none kit create <킷이름>`

이 명령어를 실행한 플레이어의 인벤토리에 모든 아이템을 config에 저장합니다

그리고 이 키트는 미니게임과 따로 저장되기 때문에 모든 미니게임에서 불러올 수 있습니다.

키트 적용 명령어 입니다.

`/fut <플레이어> kit <킷이름>`

## 위치 저장

텔레포트해야 할 위치가 필요하기 떄문에 위치를 저장할 수 있습니다.

미니게임 상수로 저장됩니다.

`/fmg set <게임이름> loc <위치이름>`

이 명령어를 실행한 플레이어의 위치를 어떤 미니게임에 상수로 저장합니다.

텔레포트 명령어 입니다.

`/fut <플레이어> teleport <게임이름> <위치이름>`

위치 이름을 wait이나 start, end로 하면 미니게임 입장시, 시작시, 퇴장시에 자동으로 텔레포트 됩니다 알아두세요!

## 블럭 리젠

미니게임 중 변경된 블럭 사항을 되돌리기 위한 기능입니다.

`/fut <player> addBlock <world> <x> <y> <z> [blocksName]`

이 명령어를 실행한 플레이어가 참여중인 미니게임 블럭 저장소에 쓰여진 좌표에 있는 블럭을 저장합니다. 만약 blocksName이 쓰여있다면, 미니게임에 그 이름으로 된 블럭 저장소를 하나 만듭니다.

gameType이 build 로 되어있을 경우 플레이어가 설치하거나 파괴하기 직전에 블록을 미니게임 블럭 저장소에 저장합니다.

블럭을 되돌리는 명령어 입니다.

`/fut none resetBlocks <게임이름> [blocksName]`

blocksName이 쓰여져 있으면 미니게임의 그 블럭 저장소에 있던 블럭으로 되돌립니다.

blocksName이 없으면 미니게임의 블럭 저장소에 있던 블럭으로 되돌립니다.

## 반복 명령

미니게임 명령어에 {allPlayer} 또는 {onlinePlayer}가 포함되어 있다면 명령어가 반복적으로 여러번 실행됩니다.

{allPlayer}는 미니게임에 참여 중인 플레이어 이름으로 계속 대체해 가면서 미니게임에 참여 중인 플레이어들의 수만큼 실행됩니다.

{onlinePlayer}는 서버에 참여 중인 플레이어 이름으로 계속 대체해 가면서 서버 플레이어들의 수만큼 실행됩니다.

`/fut <player> while {data(index)} <= 5 {do(fut {player} sendMsg private 안녕!)}`

이 명령어는 {data(index)}가 5보나 작거나 같을 때까지 {do()}안에 있는 명령어를 실행합니다.

그리고 이 while명령을 일반적인 명령번들에서 실행시킬 수는 없습니다. 왜냐하면, {data(index)} 같은 데이타 함수를 대체하는 건 명령어가 실행되기 전에 이미 대체되어서 변수가 아닌 상수로 조건에 적용되기 때문에 데이타 함수를 미리 대체하지 않는 keeped 명령 번들을 이용해야 합니다. keeped번들은 명령번들 앞에 keeped가 포함되어 있기만 하면 됩니다 **keeped**!

```yaml
joinCmd:
- fut {player} setData index 0
- fut {player} do keepedWhile
keepedWhileCmd:
- fut {player} while {data(index)} <= 5 {do(fut {player} do final && fut {player} addData index 1)}
finalCmd:
- fut {player} sendMsg public {data(index)}번째 나온 매세지
```

조심하세요, 이 명령어는 진짜로 조건이 틀리기 전까지는 절대 멈추지 않고 실행합니다. 이 명령어가 너무 오래 실행되면 서버가 터집니다.

## 아이템

아이템을 config에 저장하고 불러옵니다.

아이템이름으로 config에 아이템을 저장합니다

`/fmg set none item <아이템이름>`

아이템이름으로 config에 아이템을 불러옵니다

`/fut <player> give <아이템이름> [아이템갯수]`

플레이어에게 아이템을 줍니다. 만약 인벤토리가 꽉 차 있다면 아무 일도 일어나지 않을 겁니다.

`/fut <player> giveHand <아이템이름> [아이템갯수]`

플레이어가 손에 들고 자리에 아이템을 덮어씌웁니다.

`/fut <player> giveCursor <아이템이름> <인벤토리자리번호> [아이템갯수]`

플레이어의 인벤토리에서 번호값에 아이템을 덮어씌웁니다.


## GUI메뉴

GUI인벤토리 메뉴를 플레이어에게 띄웁니다.

인벤토리 아이템을 수정하면 인벤토리를 다시 띄워야 적용됩니다.

`/fmg set none inv create 인벤토리이름 <9|18|27|36|45|54> 인벤토리타이틀`

인벤토리를 생성합니다.

`/fmg set none inv addItem <인벤토리이름> <인벤토리번호>`

어떤 인벤토리에 들고 있는 아이템을 인벤토리번호에 저장합니다.

`/fut <player> gui <인벤토리이름>`

인벤토리메뉴를 엽니다.

`/fut <player> setGui <invName> <index> <customItemName>`

저장되어 있던 아이템을 플레이어의 GUI메뉴에 띄웁니다.

`/fut <player> setGuiItem name <invName> <index> <itemName>`

GUI메뉴에 아이템 이름을 수정합니다.

`/fut <player> setGuiItem name <invName> <index> <line> <loreName>`

GUI메뉴에 아이템 로어를 수정합니다.

***
