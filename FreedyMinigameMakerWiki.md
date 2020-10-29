# 프리디 미니게임 메이커 위키, 자습서

***

#### 어.. 어디서 부터 시작해야 할까요...? 잘 들어주실 수 있을 겁니다.

이 플러그인으로 당신만의 미니게임을 처음부터 만들고 당신의 상상력으로 커스터마이징 할 수 있습니다.  
그러니까 이 플러그인은 미니게임 개발 도구라고 볼 수 있습니다.  
이 플러그인은 게임 플레이의 특정 부분에서 명령을 실행하여 작동합니다.  
예를 들어, 만약 미니게임이 플레이중이라면 플레이어가 움직이 전에 있었던 곳 바로 밑에 있는 블럭을 없애는 명령 구문입니다.
```yaml
/fut {player} if {isPlaying} == true {do(fut {player} setBlock {world} {fromBlockX} {calc({fromBlockY}-1)} {fromBlockZ} AIR)}
```  

#### 조건 명령

**조건 명령은 데이터를 확인하고 다른 명령을 실행합니다.**

만약 값1과 값2가 같다면 명령어를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> == <값2> {do(<실행될명령>)}`  
  

만약 값1과 값2가 같고 값3과 값4가 같다면 명령어를 실행하는 명령 구문입니다.
  

`/fut <플레이어> if <값1> == <값2> fut <플레이어> if <값3> == <값4> {do(<실행될명령>)}`  
  

만약 값1과 값2가 같다면 명령1을 실행하고 또, 값3과 값4가 같다면 명령2를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> == <값2> {do(<실행될명령1>)}fut <플레이어> if <값3> == <값4> {do(<실행될명령2>)}`  
  

만약 값1과 값2가 같다면 명령1을 실행하고 만약 아니라면 명령2를 실행하고 만약 값3과 값4가 같다면 명령3을 실행하고 만약 아니라면, 명령4를 실행하는 명령 구문입니다.

`/fut <플레이어> if <값1> == <값2> {do(<실행될명령1>)}{else(<실행될명령2>)}fut <플레이어> if <값3> == <값4> {do(<실행될명령3>)}{else(<실행될명령4>)}`  
  

***

#### 실행 명령

`/fut <player> setData <customData> <data>`

`/fut <player> addData <customData> <amount>`

`/fut <player> setPlayerData <customData> <data>`

`/fut <player> addPlayerData <customData> <amount>`

`/fut <player> cancelEvent`

`/fut <player> teleport <private|team|game> <미니게임> <저장된위치>` 

`/fut <player> sendMsg <public|private|team|game> <메새지>`

`/fut <player> sendTitle <public|private|team|game> <fadeIn> <stay> <fadeOut> <제목-부제목>`

`/fut <player> sendSound <private|team|game> <사운드>`

사운드목록: https://helpch.at/docs/1.12.2/org/bukkit/Sound.html

`/fut <player> give <커스텀아이템이름>`

`/fut <player> kit <킷이름>`

`/fut <player> openGui <메뉴이름>`

`/fut <player> closeGui`

`/fut <player> join <게임이름>`

`/fut <player> executeCmd <명령줄>`

`/fut <player> executeDelayCmd <딜레이틱> <명령줄>`

`/fut <player> executeConCmd <딜레이틱> <명령줄>`

`/fut <player> resetBlocks <게임이름>`

`/fut <player> setBlock <world> <x> <y> <z> <blockType>`

`fut <player> topTpInWorldBoarder`

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

`{playerList(default)}`
미니게임에 참여중인 플레이어 이름 리스트를 대체합니다.

`{date(yyyy년 MM월 dd일)}`
현재 시각을 구해서 대체합니다.

`{length(abcd)}`
텍스트의 길이를 구해서 대체합니다.

`{replace(안녕친구들, 안녕, 잘가)}`

> 이 곳은 아직 완성되지 않았어요! 다음에 다시 찾아주세요.

#### 이벤트 번들


**이벤트 번들은 어떤 상황에서 명령들을 실행합니다**

```yaml
blockBreakCmd:
- fut {player} sendMsg private no!
- fut {player} cancelEvent
```

`preJoinCmd`
플레이어가 미니게임에 참여하기 직전에 실행됩니다

`joinCmd`
플레이어가 미니게임에 참여했을 때 실행됩니다

`preQuitCmd`
플레이어가 미니게임을 퇴장하기 직전에 실행됩니다

`quitCmd`
플레이어가 미니게임을 퇴장했을 때 실행됩니다

`conStartCmd`
미니게임이 시작됬을 때 실행됩니다

`preConEndCmd`
미니게임이 종료되기 직전에 실행됩니다

`conEndCmd`
미니게임이 종료되고 실행됩니다

`interactCmd`
미니게임에 참여 중인 플레이어가 엔티티를 제외한 무언가를 클릭하거나 상호작용했을 때 실행됩니다

`interactEntityCmd`
미니게임에 참여 중인 플레이어가 엔티티를 클릭했을 때 실행됩니다

`moveCmd:`
미니게임에 참여 중인 플레이어가 블럭 단위로 한 칸 움직였을 때 실행됩니다

`blockBreakCmd`
미니게임에 참여 중인 플레이어가 블럭을 부술 때 실행됩니다

`blockPlaceCmd`
미니게임에 참여 중인 플레이어가 블럭을 설치할 때 실행됩니다

`preDeathCmd`
미니게임에 참여 중인 플레이어가 죽기 직전에 실행됩니다

`deathCmd`
미니게임에 참여 중인 플레이어가 죽고 실행됩니다

`damagedCmd`
미니게임에 참여 중인 플레이어가 어떤 엔티티에게 데미지를 줄 때 실행됩니다

`chatCmd`
미니게임에 참여 중인 플레이어가 채팅을 칠 때 실행됩니다



