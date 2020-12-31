## FreedyMinigameMaker
이 플러그인으로 당신만의 미니게임을 처음부터 만들고 당신의 상상력으로 커스터마이징 할 수 있습니다. 그러니까 이 플러그인은 미니게임 개발 도구라고 볼 수 있습니다. 이 플러그인은 게임 플레이의 특정 부분에서 명령을 실행하여 작동합니다. 그리고 미니게임이 돌아가는데에 주요한 메커니즘을 제공하고 여러가지 기능들이 있습니다. 또한, 플러그인 기능 제안이나 오류 제보를 받습니다. 문의해주세요.

## 지원되는 기능
> 커스텀 GUi 메뉴, 커스텀 키트, 커스텀 아이템, 커스텀 위치 저장, 메세지, 타이틀, 사운드 보내기, 미니게임 커맨드의 다양한 구문 지원, 미니게임의 타이머 기능 지원, 미니게임 데이타, 플레이어 데이타 미니게임 변수 지원, 수학 연산 지원, 그리고 더 많은 기능들 ...

## English Wiki  [>> 영어위키링크 <<](./EnglishWiki)

## 다운로드   [>> 다운로드링크 <<](https://github.com/FreedyPlugins/FreedyMinigameMaker/releases/latest/download/FreedyMinigameMaker.jar)

## 제안 및 버그 [>> 제보하기링크 <<](https://github.com/FreedyPlugins/FreedyPlugins/issues/new/choose)
  
## 소스코드 [>> 소스코드링크 <<](https://github.com/FreedyPlugins/FreedyMinigameMaker/tree/master/FreedyMinigameMaker)
  
***

#### 실행 명령

미니게임 유틸리티 명령어는 미니게임을 실행하는데 필요한 기능을 가지고 있습니다. 사용법을 확인하려면 게임에서 fut 명령어를 입력해보세요.

#### 인게임 테스트 

`/fut <player> sendMsg private {math(add, 2, 2)}` 플레이어로 실행한 명령은 데이타 함수가 작동하지 않습니다 

`/fut <player> execute fut {player} sendMsg private {math(add, 2, 2)}` 그래서 이렇게 해주면 가능합니다.

***


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
  테스트:
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
  테스트:
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

`/fmg join <미니게임>`
freedyminigamemaker.join 권한과 함께 이 명령을 실행한 플레이어를 미니게임에 참여시킵니다.

`/fmg quit`
freedyminigamemaker.quit 권한과 함께 이 명령을 실행한 플레이어를 퇴장시킵니다.

`/fmg create <gameName> <maxPlayers> <maxStartPlayers> <waitForStartTime>`
비어 있는 미니게임을 생성합니다.

`/fmg list`
미니게임 목록을 봅니다.

`/fmg reload`
config.yml 과 settings.yml 을 리로드합니다.

`/fmg quitAllGames`
모든 미니게임이 종료됩니다.`

`/fut <player> join <gameName>`
플레이어를 미니게임에 참여시킵니다.
  
`/fut <player> move <gameName`
플레이어를 미니게임으로 강제 이동 시킵니다.

`/fut <player> joinAll <gameName>`
미니게임에 참여 중이지 않은 모든 온라인 플레이어들을 미니게임에 참여시킵니다.

`/fut <player> kick`
플레이어를 미니게임에서 퇴장시킵니다.

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

플레리어로 실행됬거나, 커맨드블럭으로 실행됬을 때 대체되지 않는 데이타 함수를 대체하기 위해 사용되며, 플레이어가 참여 중인 미니게임으로 데이타 함수를 대체해서 <command> 명령을 실행합니다.

`/fut <player> executeConCmd <command>`
그저 콘솔에서 명령을 실행합니다.

`/fut <player> executeCmd <command>`
플레이어로 명령을 실행합니다.

`/fut <player> executeConDelayCmd <tick> <command>`
틱 후 콘솔에서 명령을 실행합니다.

`/fut <player> executeDelayCmd <tick> <command>`
틱 후 플레이어로 명령을 실행합니다.



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

#### 데이타 함수


## 구문이란?
이 플러그인에는 많은 구문이 있습니다.
여기서 잠깐!
여기서 구문이란 무엇일까요.
구문은 `{playerName}` 이라고 쓰면 `플레이어 이름`이 출력되는 그런 것 입니다.

`{gameName}` 하면 미니게임 이름이 나오고,
`{playerAmount}` 하면 플레이어 수가 나오겠죠?

이제 예제를 한번 봅시다.

`/tp {player} 0 0 0`
이 명령을 실행했다고 가정합시다.
그러면 `{player}`자리에 `이 명령어를 실행한 플레이어의 이름'으로 교체 됩니다.
물론 `/tp` 명령이 실제로 그렇지는 않지만요.
하지만! 이 구문은 프리디미니게임메이커 플러그인에서는 작동합니다.
그치만! `/tp` 명령이 좀 더 복잡하게 되어 있어요. 한번 살펴볼까요?

`/fut {player} teleport private testGame start`

이렇게 되어 있네요..

제가 해석해보겠습니다.

`/fut {player} teleport private testGame start`
플레이어 티피한다 개인적으로 testGame 미니게임에 저장되어 있는 start 위치로


> 구문을 테스트 하기 위해서는 아래와 같은 명령어로 테스트해보세요! {allPlayer} {onlinePlayer}는 미니게임 config에서만 작동합니다
 
`/fut <player> execute fut {player} sendMsg private {x}`
  

## 구문 리스트

### `{allPlayer}` 
미니게임에 참여중인 모든 플레이어 이름으로 대체합니다.
이 구문이 있는 명령어는 미니게임에 참여 중인 플레이어 수만큼 실행됩니다.

### `{onlinePlayer}` 
서버에 참여중인 모든 플레이어 이름으로 대체합니다.
이 구문이 있는 명령어는 서버에 참여 중인 플레이어 수만큼 실행됩니다.

### `{playerName}` 또는 `{player}` (둘다 같음)
이 명령어를 발동되게 한 원인의 플레이어의 이름으로 대체됩니다.

### `{playerIndex}`
이 명령어를 발동되게 한 원인의 플레이어의 참여중인 플레이어 목록 나열 번호로 대체합니다.

### `{maxPlayers}`
미니게임 입장 최대 인원을 대체합니다.

### `{randomPlayer}`
미니게임에 참여 중인 플레이어중 랜덤으로 하나를 뽑은 플레이어의 이름을 대체합니다.

### `{playerAmount}`
미니게임 시작 당시, 참여 중인 플레이어 수를 대체합니다.

### `{playerSize}`
미니게임에 참여 중인 플레이어의 수를 대체합니다.

### `{isPlaying}`
미니게임이 플레이 중인지 아닌지 여부를 대체합니다. 참이면 true, 거짓이면 false

### `{isWaiting}`
미니게임이 플레이를 위해 대기 중인지 아닌지 여부를 대체합니다. 참이면 true, 거짓이면 false

### `{game}` 또는 `{gameName}` (둘다 같음)
콘피그파일에 저장된 미니게임 이름을 대체합니다.

### `{gameType}`
미니게임의 타입을 대체합니다.

### `{randomNumer}`
0부터 1 사이에 유리수인 난수를 생성합니다. Math.random() 입니다.

### `{playerIsOp}`
플레이어가 오피가 있으면 true, 없으면 false

### `{playerUuid}`
플레이어의 UUID를 대체합니다.

### `{x}`
플레이어의 X좌표를 대체합니다.

### `{y}`
플레이어의 Y좌표를 대체합니다.

### `{z}`
플레이어의 Z좌표를 대체합니다.

### `{eyeX}`
플레이어의 관점의 위치의 X좌표를 대체합니다.

### `{eyeY}`
플레이어의 관점의 위치의 Y좌표를 대체합니다.

### `{eyeZ}`
플레이어의 관점의 위치에 Z좌표를 대체합니다.

### `{yaw}`
플레이어의 요값을 대체합니다.

### `{pitch}`
플레이어의 피치값을 대체합니다.

### `{world}`
플레이어가 있는 월드이름을 대체합니다.

### `{playerName}`
플레이어의 이름을 대체합니다. {player}와 같습니다.

### `{playerCursor}`
플레이어의 손이 있는 칸의 위치를 대체합니다.

### `{playerIndex}`
플레이어가 미니게임에서 몇번째 플레이어 인지 대체합니다 1부터 시작하지 않고 0부터 시작해서 매깁니다.

### `{playerHealth}`
플레이어의 체력을 대체합니다.

### `{playerHealth}`
플레이어의 체력을 대체합니다.

### `{playerFood}`
플레이어의 배고픔을 대체합니다

### `{playerExp}`
플레이어의 경험치를 대체합니다.

### `{playerIsBlocking}`
플레이어가 블럭을 부수고 있는지 대체합니다.

### `{playerIsLeashed}`
플레이어가 달리고 있는지 대체합니다.

### `{playerIsSneaking}`
플레이어가 움크리고 있는지 대체합니다.

### `{playerIsGliding}`
플레이어가 겉날개를 달고 글라이딩 중 인지 대체합니다.

### `{playerIsSwimming}`
플레이어가 수영 중인지 대체합니다.

### `{playerIsSleeping}`
플레이어가 침대에서 잠 자고 있는지 대체합니다.

### `{math(add, 1, 2)}`
1 더하기 2 의 값을 대체합니다. add이외에 remainder, multiply, divide 이 있습니다

### `{playerData(testData)}`
따로 저장되어 있던 플레이어 데이타로 대체합니다.

### `{data(testData)}`
따로 저장되어 있던 미니게임 데이타로 대체합니다.

### `{miniGamedata(테스트, isPlaying)}`

테스트 미니게임이 시작되었는지 출력합니다. isPlaying 대신 playerList 로 미니게임에 참여중인 플레이어들을 모두 출력할 수도 있습니다. 그 외에는 따로 저장되어있던 미니게임 데이타로 대체합니다

### `{color(&a안녕하세요)}`
초록색 글씨로 대체합니다

### `{numeric(1004)}`
1004 라는 숫자가 숫자인지 아닌지를 대체합니다

### `{entityLoc(ce5e7f96-6c5d-43c1-a948-1c8c2388e47a)}`
Uuid의 엔티티의 위치를 대체합니다

### `{topLoc(world, 10, 5, -1)}`
위 좌표에 있는 블럭의 y좌표중에 가장 높은 위치에 있는 블럭좌표를 대체합니다

### `{contain(ㅁ, ㄱ, ㄴ, ㄷ, ㄹ, ㅁ)}`
ㄱ, ㄴ, ㄷ, ㄹ, ㅁ 중에서 ㅁ 이 있는지를 대체합니다

### `{softContain(e, Hello, My name is Bruce)}`
"Hello, My name is Bruce" 에서 영어 e가 포함되어 있는지 대체합니다

### `{sub(1, 3, 안녕하세요)}`
안녕하세요 문자열의 1 부터 3까지 잘라서 녕하세를 대체합니다

### `{blockName(world, 10, 5, -1)}`
위 좌표에 있는 블럭의 코드를 대체합니다 

### `{playerList(default)}`
미니게임에 있는 플레이어 이름을 모두 출력합니다. default가 아닌 all 이라면 모든 온라인 플레이어의이름을 모두 대체합니다.

### '{add(사, 일, 이, 삼)}`
일, 이, 삼에 사를 추가한 목록을 출력합니다.

### `{remove(일, 일, 이, 삼)}`
일, 이, 삼에 일을 제거한 목록을 출력합니다.

### `{file(playerPoint-ce5e7f96-6c5d-43c1-a948-1c8c2388e47a)}`
위 UUID 앞에 playerPoint가 붙여진 값을 data.yml 에서 찾아옵니다. 만약 그 값이 없다면 none이 출력됩니다. 문자와 문자 사이에 점(.)을 붙이면 앞에 있는 문자 속에 뒤에있는 문자가 저장됩니다. UUID만 점 앞에 붙이면 오류가 나므로 UUID앞에 아무 문자나 붙여야 합니다.

### `{date(<날짜포멧>)}`
https://nowonbun.tistory.com/502

### `{length(abcde)}`
abcde의 문자길이(5)를 출력합니다.

### `{indexOf(0, 10, 20, 30)}`
10, 20, 30 중에 0 번째에 오는 데이타를 대체합니다.

### `{valueOf(20, 10, 20, 30)}`
10, 20, 30 중에 20 데이타의 index를 대체해서 2를 대체합니다.

### `{sizeOf(일, 이, 삼, 사)}`
일, 이, 삼, 사의 목록의 갯수를 대체합니다.

### `{shuffle(1, 2, 3)}`
1, 2, 3의 나열순서를 섞어서 대체합니다.

### `{highList(1, 2, 3)}`
가장 큰 순서대로 나열한 3, 2, 1을 대체합니다.

### `{flip(3, 1, 2)}`
순서를 뒤집어 2, 1, 3을 대체합니다.

### `{lowestNumber(1, 2, 3)}`
가장 적은 숫자를 대체합니다.

### `{highestNumber(1, 2, 3)}`
가장 많은 숫자를 대체합니다.

### `{randomNumber(0, 9)}`
0부터 9까지 숫자 중에 하나를 골라 대체합니다.

### `{random(apple, bread, cheese)}`
apple, bread, cheese 충에 하나를 골라 대체합니다.

### `{constant(testMessage)}`
콘피그파일에 저장되어 있던 미니게임 상수로 대체합니다.

### `{playerTargetBlock(100)}`
플레이어가 100블럭 범위안에서 바라보고 있는 블럭의 위치를 대체합니다.

### `{playerTargetEntity(100)}`
플레이어가 100블럭 범위 안에서 바라보고 있는 엔티티의 위치를 대체합니다.

### `{hasPerm(perm.command)}`
플레이어가 권한이 있는지를 대체합니다.

### `{itemAmount(1)}`
플레이어의 인벤토리에 1번째 칸 아이템 갯수를 출력합니다.

### `{itemType(1)}`
플레이어의 인벤토리에 1번째 칸 아이템 타입을 출력합니다.

### `{replace(안녕, 안녕하세요, 방가워, 잘지내, 안녕, 잘가, 친구들)}`
방가워, 잘지내, 안녕, 잘가, 친구들 중에 안녕을 안녕하세요로 모두 바꾼 목록을 대체합니다.

### `{integer(3.1415926535897932384626)}`
위 수의 소수점을 없앤 3을 대체합니다.

### `{abs(-7)}`
-7에 마이너스 부호가 있다면 제거한 값인 7을 대체합니다.

### `{cos(3)}`
3의 코사인값을 대체합니다.

### `{sin(3)}`
3의 사인 값을 대체합니다.

### `{tan(3)}`
3의 탄젠트 값을 대체합니다.

### `{round(3.5)}`
3.5를 반올림한 값인 4를 대체합니다.

### `{roundUp(3.5)}`
3.5를 올림한 값인 4를 대체합니다.

### `roundDown(3.5)}`
3.5를 내림한 값인 3을 대체합니다.



***


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

`interactCmd` `{actionName} {action} {itemName} {itemAmount} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 엔티티를 제외한 무언가를 클릭하거나 상호작용했을 때 실행됩니다.

`interactEntityCmd` `{entityName} {entityType} {itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 엔티티를 클릭했을 때 실행됩니다.

`itemConsumeCmd`
미니게임에 참여 중인 플레이어가 음식을 먹거나 아이템을 사용했을 때 실행됩니다.

`PlayerInventoryClickCmd` `{slot} {invType} {clickType}`
플레이어가 저장되어 있는 인벤토리를 클릭했을 때 실행됩니다.

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

`damagedCmd` `{entityName} {entityType} {itemName} {itemAmount} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 어떤 엔티티에게 데미지를 줄 때 실행됩니다.

`damageCmd` `{cause}`
미니게임에 참여 중인 플레이어가 데미지를 입었을 때 실행됩니다.

`projectileCmd` `{cause} {damage} {projectileType} {projectileName} {projectileUuid} {entityName} {entityType}`
미니게임에 참여 중인 플레이어가 발사체로부터 데미지를 입었을 때 실행됩니다.

`projectileHitCmd` `{projectileType} {projectileName} {projectileUuid} {entityName} {entityType} {blockType} {blockX} {blockY} {blockZ} {blockFace}`
발사체가 엔티티나 블럭에 닿았을 때 실행됩니다.

`itemHeldCmd` `{newSlot} {previousSlot}`
플레이어가 9칸 핫바 슬롯을 바꿀 때 실행됩니다.

`swapHandCmd` `{itemName} {itemAmount} {itemDurability} {itemType} {offItemName} {offItemAmount} {offItemDurability} {offItemType}`
플레이어가 F 키를 통해서 아이템을 대체할 때 실행됩니다.

`sneakCmd` 
플레이어가 SHIFT 키를 통해 움크릴 떄 실행됩니다.

`dropCmd` `{itemName} {itemAmount} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 아이템을 떨굴 때 실행됩니다.

`pickupCmd` `{itemName} {itemAmount} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 아이템을 주울 때 실행됩니다.

`chatCmd` `{format} {chat}`
미니게임에 참여 중인 플레이어가 채팅을 칠 때 실행됩니다.

`commandCmd` `{command} {args}`
미니게임에 참여 중인 플레이어가 명령어를 칠 때 실행됩니다.

`worldChangeCmd` `{fromWorld} {toWorld}`
미니게임에 참여 중인 플레이어가 월드를 이동할 때 실행됩니다.

`fishingThrowCmd` `{entityUuid} {entityName} {entityType} {hookLoc}`
낚시대를 던질 때 실행됩니다.

`fishingBackCmd` `{entityUuid} {entityName} {entityType} {hookLoc}`
낚시대를 회수할 때 실행됩니다.

`vehicleDamageCmd` `{vehicleName} {vehicleType}`
미니게임에 참여 중인 플레이어가 보트나 카트에게 대미지를 줄 때 실행됩니다.

`vehicleExitCmd` `{vehicleName} {vehicleType}`
미니게임에 참여 중인 플레이어가 보트나 카트를 타고 있다가 내릴 때 실행됩니다.

`vehicleCollisionCmd` `{vehicleName} {vehicleType}`
미니게임에 참여 중인 플레이어가 타고 있는 보트나 카트가 엔티티와 충돌할 때 실행됩니다.

`명령번들이름Cmd` `{커스텀함수}`
`/fut <미니게임플레이어> do 명령번들이름 커스텀함수1, 값1, 커스텀함수2, 값2 ...`
do 실행 명령을 통해서 실행됩니다.

`keeped명령번들이름Cmd` `{커스텀함수}`
`/fut <미니게임플레이어> do keeped명령번들이름 커스텀함수1, 값1, 커스텀함수2, 값2 ...`
do 실행 명령을 통해서 실행됩니다. keeped번들은 데이타 함수가 대체되지 않습니다. 그래서 무의미한 /fut <player> execute fut <player> ... 구문을 앞에 붙여서 데이타 함수를 대체해야 합니다. 그리고 또한, {player} 구문도 대체가 되지 않기 떄문에, do 명령을 통해 커스텀함수를 추가해야 합니다. /fut <player> do keepedTestBundle player, {player} 이렇게 keepedTestBundleCmd명령번들을 실행합니다. 이러한 keeped번들의 장점은 while 구문에서 데이타 함수를 매주기마다 새롭게 불러올 수 있고, 또 allPlayer 데이타 함수의 반복 구문에서 새롭게 데이타를 불러올 수 있습니다.

`메뉴이름ClickCmd` `{slot}`
어떤 메뉴이름의 GUI메뉴를 클릭했을 때 그 클릭한 위치 {slot}으로 명령번들을 실행합니다.


config 예제

빙고 미니게임 1.16.4 전용: https://pastebin.com/raw/Nqp5q3Zk

> 이 곳은 아직 완성되지 않았어요! 다음에 다시 찾아주세요..



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
