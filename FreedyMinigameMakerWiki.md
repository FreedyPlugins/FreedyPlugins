
# 프리디미니게임메이커 설명서

이 플러그인으로 당신만의 미니게임을 처음부터 만들고 당신의 상상력으로 커스터마이징 할 수 있습니다.  
그러니까 이 플러그인은 미니게임 개발 도구라고 볼 수 있습니다.  
이 플러그인은 게임 플레이의 특정 부분에서 명령을 실행하여 작동합니다.  
예를 들어, 만약 미니게임이 플레이중이라면 플레이어가 움직이 전에 있었던 곳 바로 밑에 있는 블럭을 없애는 명령 구문입니다.

```yaml
/fut {player} if {isPlaying} == true fut {player} setBlock {world} {fromBlockX} {math(add, {fromBlockY}, -1)} {fromBlockZ} AIR
```  

또다시 예를 들어 보면, 만약 미니게임이 플레이중이지 않고, 플레이어가 5명이라면 게임이 시작되었다고 알리는 구문입니다.
```yaml
/fut {player} if {isPlaying} == false fut {player} if {playerSize} >= 5 fut {player} sendMsg game 게임이 시작되었습니다!
```  

네 예제는 많아요.

하지만 이제서 중요한 건 이 구문을 어떻게 쓰는 것인가 입니다.

미니게임 중에 많은 이벤트가 존재합니다!

플레이어가 미니게임에 참여할때, 퇴장할떄,

미니게임이 시작될 때, 미니게임이 끝날 때.

그리고 여러 이벤트를 직접 만드실 수 있어요!

미니게임이 실행 중일 때마다 구문이 작동되게 하는 반복이벤트도 있습니다!

음 좋아요! 미니게임을 생성해봅시다.

군말없이 알려드리죠.

 > 경고! 명령어의 대소문자를 지키세요.
 
 `/fmg set <게임이름> needClearInv true` 미니게임참여할 때 인벤토리를 비워야만한다면 이 명령어 입력

`/fmg create <게임이름> <최대인원> <시작인원> <시작대기초>` 미니게임 한개 생성

`/fmg set <게임이름> wait` 미니게임 입장시 위치 설정 - 안해도 됨

`/fmg set <게임이름> start` 미니게임 시작시 위치 설정 - 안해도 됨

`/fmg set <게임이름> end` 미니게임 종료시 위치 설정 - 안해도 됨

`/fmg set none kit create <킷이름>` 전투용 키트제작

`/fmg set none kit create empty` 미니게임 끝날 때 적용하는 인벤토리 키트 제작 (없다면 빈 인벤토리로 꼭 해야 함)

`/fmg set <게임이름> setCmd conStartCmd fut {player} sendTitle game 10 20 10 {color(&aFIGHT!)}`

`/fmg set <게임이름> setCmd conStartCmd fut {allPlayer} kit <킷이름>`

`/fmg set <게임이름> setCmd preDeathCmd fut {player} cancelEvent`

`/fmg set <게임이름> setCmd preDeathCmd fut {player} sendMsg game {player}이(가) 죽었습니다`

`/fmg set <게임이름> setCmd preDeathCmd fut {player} setPlayerData dead true`

`/fmg set <게임이름> setCmd preDeathCmd fut {player} do keepedWinner player, {player}`

`/fmg set <게임이름> setCmd keepedWinnerCmd fut {player} setData alivePlayers 0`

`/fmg set <게임이름> setCmd keepedWinnerCmd fut {player} executeConCmd fut {allPlayer} if {playerData(dead)} /= true fut {player} addData alivePlayers 1`

`/fmg set <게임이름> setCmd keepedWinnerCmd fut {player} executeConCmd fut {allPlayer} if {playerData(dead)} /= true fut {player} setData p {allPlayer}`

`/fmg set <게임이름> setCmd keepedWinnerCmd fut {player} if {integer({data(alivePlayers)})} == 1 fut {player} do stop player, {data(p)}`

`/fmg set <게임이름> setCmd stopCmd fut {player} sendMsg public {data(p)}이(가) {game}을 승리했습니다!`

`/fmg set <게임이름> setCmd stopCmd fut {player} shutDown`

`/fmg set <게임이름> setCmd quitCmd fut {player} kit empty`

이제 구문을 어떻게 사용하고 이벤트에 구문을 어떻게 적용하는지 알려드리겠습니다.



#### 조건 명령

**조건 명령은 데이터를 확인하고 다른 명령을 실행합니다.**

만약 값1과 값2가 같다면 명령어를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> == <값2> <실행될명령>`  


만약 값1과 값2가 같지 않다면 명령어를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> /= <값2> <실행될명령>` 


만약 값1이 값2보다 작다면 명령어를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> < <값2> <실행될명령>` 


만약 값1이 값2보다 크다면 명령어를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> > <값2> <실행될명령>` 

  
만약 값1이 값2보다 작거나 같으면 명령어를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> <= <값2> <실행될명령>` 


만약 값1이 값2보다 크거나 같으면 명령어를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> >= <값2> <실행될명령>` 


만약 값1과 값2가 같고 값3과 값4가 같다면 명령어를 실행하는 명령 구문입니다.
  

`/fut <플레이어> if <값1> == <값2> fut <플레이어> if <값3> == <값4> <실행될명령>`  
  

만약 값1과 값2가 같다면 명령1과 명령2를 실행하는 구문입니다
  

`/fut <플레이어> if <값1> == <값2> {do(<명령1> && <명령2>)}`  
  

만약 값1과 값2가 같다면 명령1과 명령2를 실행하고 값1과 값2가 같지 않다면 명령3과 명령4를 실행하는 구문입니다
  

`/fut <플레이어> if <값1> == <값2> {do(<명령1> && <명령2>)}{else(<명령1> && <명령2>)}`  

> 알림! {do()}나 {else()} 구문에서 여러 명령을 실행하려면 명렁과 명령 사이에 ' && ' (공백과 공백 사이에 '&&'를 넣은 문자열)을 넣어주세요

```yaml
fut {player} if true == true {do(fut {Player} sendMsg public 안녕하세요! && fut {player} sendMsg public 어서오세요!)}
```

>> 주의! {do()}나 {else()} 구문 속에 {add()}나 {data()} 같은 데이타 함수를 넣으면 안되요! fut <player> do player, <player> 실행 명령을 통해 데이타 함수를 사용하세요
  
***

#### 실행 명령

`/fut <player> setData <customData> <data>`

`/fut <player> addData <customData> <amount>`

`/fut <player> setPlayerData <customData> <data>`

`/fut <player> addPlayerData <customData> <amount>`

`/fut <player> cancelEvent`


`/fut <player> teleport <private|game> <미니게임> <저장된위치>` 

`/fut <player> sendMsg <public|private|game> <메새지>`

`/fut <player> sendTitle <public|private|game> <fadeIn> <stay> <fadeOut> <제목-부제목>`

`/fut <player> sendActionBar <public|private|game> <메새지>`

`/fut <player> sendBossBar <private|game> <customName> <progress> <color> <message|none>`

`/fut <player> sendSound <private|game> <사운드>`

사운드목록: https://helpch.at/docs/1.12.2/org/bukkit/Sound.html

`/fut <player> addPotion <private|game> <포션>`

`/fut <player> removePotion <private|game>`

`/fut <player> gameMode <private|game> <CREATIVE|SURVIVAL|SPECTATOR|ADVENTURE>`

`/fut <player> food <private|game> <배고픔게이지>`

`/fut <player> health <private|game> <체력 게이지>`

`/fut <player> gui <메뉴이름>`

`/fut <player> give <커스텀아이템이름>`

`/fut <player> giveHand <커스텀아이템이름>`

`/fut <player> give <커스텀아이템이름>`

`/fut <player> cursor <커서번호>`

`/fut <player> kit <킷이름>`

`/fut <player> openGui <메뉴이름>`

`/fut <player> closeGui`

`/fut <player> knockBack <x> <y> <z>`

`/fut <player> join <게임이름>`

`/fut <player> joinAll <게임이름>`

`/fut <player> kick`

`/fut <player> executeCmd <명령줄>`

`/fut <player> executeDelayCmd <딜레이틱> <명령줄>`

`/fut <player> executeConCmd <명령줄>`

`/fut <player> executeConDelayCmd <딜레이틱> <명령줄>`

`/fut <player> resetBlocks <게임이름>`

`/fut <player> setBlock <world> <x> <y> <z> <blockType>`

`/fut <player> while <조건1> == <조건2> {do(<명령1> && <명령2>)}`

`/fut <player> if <조건1> == <조건2> {do(<명령1> && <명령2>)}{else(<명령1> && <명령2>)}`

`/fut <player> do <명령번들> 함수이름, 함수값, 함수이름2, 함수값2 ...`

`/fut <player> setFile <파일이름> <데이타>`

`/fut <player> saveFile`

`/fut <player> nearByEntities <x> <y> <z> <cmd>`

`/fut <player> conLog <message>`

***

#### 데이타 함수

`{allPlayer}` 
미니게임에 참여중인 모든 플레이어 이름으로 대체합니다.
이 구문이 있는 명령어는 미니게임에 참여 중인 플레이어 수만큼 실행됩니다.

`{playerName}` 또는 `{player}` (둘다 같음)
이 명령어를 발동되게 한 원인의 플레이어의 이름으로 대체됩니다.

`{playerIndex}`
이 명령어를 발동되게 한 원인의 플레이어의 참여중인 플레이어 목록 나열 번호로 대체합니다.

`{maxPlayers}`
미니게임 입장 최대 인원을 대체합니다.

`{randomPlayer}`
미니게임에 참여 중인 플레이어중 랜덤으로 하나를 뽑은 플레이어의 이름을 대체합니다.

`{playerAmount}`
미니게임 시작 당시, 참여 중인 플레이어 수를 대체합니다.

`{playerSize}`
미니게임에 참여 중인 플레이어의 수를 대체합니다.

`{isPlaying}`
미니게임이 플레이 중인지 아닌지 여부를 대체합니다. 참이면 true, 거짓이면 false

`{isWaiting}`
미니게임이 플레이를 위해 대기 중인지 아닌지 여부를 대체합니다. 참이면 true, 거짓이면 false

`{game}` 또는 `{gameName}` (둘다 같음)
콘피그파일에 저장된 미니게임 이름을 대체합니다.

`{gameType}`
미니게임의 타입을 대체합니다.

`{blockName(world, 10, 2, -10)}`
world라는 이름의 월드에 좌표 10 2 -10에 있는 블럭 코드를 대체합니다.

`{calc(1+2+3)}`
1 더하기 2 더하기 3 의 값을 대체합니다.

`{lowestNumber(1, 2, 3)}`
가장 적은 숫자를 대체합니다.

`{highestNumber(1, 2, 3)}`
가장 많은 숫자를 대체합니다.

`{playerData(testData)}`
따로 저장되어 있던 플레이어 데이타로 대체합니다.

`{data(testData)}`
따로 저장되어 있던 미니게임 데이타로 대체합니다.

`{constant(testMessage)}`
콘피그파일에 저장되어 있던 데이타로 대체합니다.

`{random(apple, bread, cheese)}`
apple, bread, cheese 충에 하나를 골라 대체합니다.

`{randomNumber(0, 9)}`
0부터 9까지 숫자 중에 하나를 골라 대체합니다.

`{shuffle(1, 2, 3)}`
1, 2, 3의 나열순서를 섞어서 대체합니다.

`{indexOf(0, 10, 20, 30)}`
10, 20, 30 중에 0 번째에 오는 데이타를 대체합니다.

`{valueOf(20, 10, 20, 30)}`
10, 20, 30 중에 20 이라는 데이타의 나열 번호를 대체합니다

`{sizeOf(일식이, 두식이, 세식이)}`
일식이, 두식이, 세식이 데이타들의 개수를 대체합니다

`{suffle(1, 2, 3, 4, 5)}`
1, 2, 3, 4, 5를 섞어서 2, 3, 5, 1, 4처럼 랜덤으로 대체합니다

`{highList(1, 4, 2, 5, 3)}`
1, 4, 2, 5, 3을 크기가 큰 숫자부터 나열해서 대체합니다

`{flip(1, 2, 3, 4, 5)}`
1, 2, 3, 4, 5의 순서를 거꾸로 뒤집어 5, 4, 3, 2, 1로 대체합니다

`{constant(testMsg)}`
config.yml 파일에 미니게임 데이타에서 testMsg 값을 대체합니다

`{integer(1.0)}`
1.0의 소수점을 없앤 1을 대체합니다

`{round(1.3)}`
소수 1.3을 반올림해서 1을 대체합니다

{roundDown(1.3)}
소수 1.3을 내림해서 1을 대체합니다

{roundUp(1.3)}
소수 1.3을 올림해서 2를 대체합니다

`{playerList(default)}`
미니게임에 참여중인 플레이어 이름 리스트를 대체합니다.

`{date(yyyy년 MM월 dd일)}`
현재 시각을 구해서 대체합니다.

`{length(abcd)}`
텍스트의 길이를 구해서 대체합니다.

`{replace(이, 백, 이종원)}`
이종원에서 '이'자를 '백'자로 대체한 값을 대체합니다.

`{remove(하세요, 안녕하세요)}`
'안녕하세요'에서 '하세요'를 삭제한 값을 대체합니다.

`{file(testFile)}`
플러그인 폴더에 data.yml 파일에 있는 testFile 값을 가져옵니다.

`{contain(쿠키, 똥, 종이, 아이패드, 쿠키, 게임)}`
똥, 종이, 아이패드, 쿠키, 게임에서 쿠키가 포함되어 있는지에 여부를 대체합니다

`{sub(1, 3, 안녕하세요방갑습니다)}`
안녕하세요방갑습니다에서 '녕하세'를 대체합니다

`{numeric(123)}`
123이 숫자임 여부를 대체합니다

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

`preDeathCmd` `{killerType} {killerName}`
미니게임에 참여 중인 플레이어가 죽기 직전에 실행됩니다.

`deathCmd` `{killer}`
미니게임에 참여 중인 플레이어가 죽고 실행됩니다.

`damagedCmd` `{entityName} {entityType} {itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 어떤 엔티티에게 데미지를 줄 때 실행됩니다.

`damageCmd` `{cause}`
미니게임에 참여 중인 플레이어가 데미지를 입었을 때 실행됩니다.

`dropCmd` `{itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 아이템을 떨굴 때 실행됩니다.

`pickupCmd` `{itemName} {itemDurability} {itemType}`
미니게임에 참여 중인 플레이어가 아이템을 주울 때 실행됩니다.

`chatCmd` `{format} {chat}`
미니게임에 참여 중인 플레이어가 채팅을 칠 때 실행됩니다.

`commandCmd` `{command} {args}`
미니게임에 참여 중인 플레이어가 명령어를 칠 때 실행됩니다.

`명령번들이름Cmd` `{커스텀함수}`
`/fut <미니게임플레이어> do 명령번들이름 커스텀함수1, 값1, 커스텀함수2, 값2 ...`
do 실행 명령을 통해서 실행됩니다.

`keeped명령번들이름Cmd` `{커스텀함수}`
`/fut <미니게임플레이어> do keeped명령번들이름 커스텀함수1, 값1, 커스텀함수2, 값2 ...`
do 실행 명령을 통해서 실행됩니다 keeped번들은 데이타 함수가 대체되지 않습니다. 그래서 무의미한 /fut <player> if true == true 구문을 앞에 붙여서 데이타 함수를 대체해야 합니다.
이러한 keeped번들의 장점은 while 구문에서 데이타 함수를 매주기마다 새롭게 불러올 수 있고, 또 allPlayer 데이타 함수의 반복 구문에서 새롭게 데이타를 불러올 수 있습니다.

> 이 곳은 아직 완성되지 않았어요! 다음에 다시 찾아주세요..
