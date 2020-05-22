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


> 이 곳은 아직 완성되지 않았어요! 다음에 다시 찾아주세요.
