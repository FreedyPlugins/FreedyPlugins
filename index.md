# 안녕하세요. 종원입니다.
저는 마인크래프트 플러그인을 야매로 배운 프로그래머 입니다.  
경기도에 살고 있고 2021년으로 고1입니다.  
미니게임을 만들기 위해 다양한 플러그인을 사용했지만,   
사용하기 너무 어려워서 그냥 미니게임 메이커를 만들었습니다.

---

프리디 미니게임 메이커 2는 스크립트 형식의 미니게임 제작 플러그인입니다.  
명령을 실행하는 것이 기본 원리 입니다.

```
on move 
    print "당신은 움직였습니다!"
```
이딴 식으로 작동합니다.

```
on move {
    print ( "당신은 움직였습니다!" )
}

```
위 아래에 있는 소스코드 모두 잘 됩니다.  
이 코드는 플레이어가 움직이면 매세지를 보내는 겁니다.

여기에 `print`는 `명령`이라고 부릅니다  
그리고 `on move` 에 `move`는 `이밴트`라고 불러요.  
중괄호 안에 있는 명령, 또는  이벤트 아래에 있는 명령을 `번들` 이라고 부릅니다.  
그리고 이런 것들을 총칭해서 `소스코드`, `코드`, `구문` 이라고 부릅니다.

`move` 는 움직였을 때 아래 코드를 실행하겠다는 `이벤트` 입니다.  
`print` 는 플레이어에게 다음 매세지를 보내겠다는 `명령`입니다.  
`{ }` `( )` 소괄호와 중괄호는 구문이 어디까지 써있는지 표시해주는 것입니다.  
`""` `''` 따옴표는 명령이 아닌 매세지 문자를 구분하기 위해 표시해주는 겁니다.

중괄호와 소괄호는 앞뒤에 공백 띄어쓰기가 있어야 합니다.  
`print("안녕")`(X) `print ( "안녕" )`(O)  
`{print "안녕"}`(X) `{ print "안녕" }`(O)

---

## 미니게임과 명령어

저는 `미니게임`을 `게임`으로 부르겠습니다.  
서버에 입장 했을 때 자동으로 참여되는 게임인 허브 게임이 있습니다.  
이 게임은 서버를 나가는 방법 이외에는 나갈 수 없습니다.  
허브 게임이 아닌 게임에 참여하려면 허브 게임이 아닌 게임에 참여해 있지 않아야 합니다.

`/fmg create <게임이름>` 게임을 생성합니다. 게임이름에 허용되지 않는 문자를 포함하면 안됩니다. 띄어쓰기는 허용됩니다.

`/fmg delete <게임이름>` 게임을 삭제합니다.

`/fmg reload [게임이름]` 모든 게임 또는 특정 게임 파일을 리로드 합니다.

`/fmg join <게임이름>` 게임에 참여합니다.

`/fmg quit <게임이름>` 게임을 떠납니다.

`/fmg save` 변수를 저장합니다.

`/fmg game` 존재하는 게임 목록을 보여줍니다.

`/fmg do <번들이름>` 허브 게임에 번들을 실행합니다.

`/fmg run <명령>` 명령을 작동 시킵니다.

---

## 데이타

변수, 저장할 수 있는 값이죠. 우리는 이것을 `데이타` 라고 부릅니다.   
데이타는 총 3가지 종류의 장소에 저장할 수 있습니다.  
파일, 게임, 그리고 플레이어로 3개의 메모리에 저장할 수 있습니다.  
`데이타`의 명령 키워드는 `data 또는 var` 입니다. 두개다 잘 됩니다.      
파일 데이타라면 `all 또는 online` 키워드를 `데이타`에 붙이면 됩니다. `all data`    
게임 데이타라면 `game` 키워드를 `데이타`에 붙이면 됩니다. `game data`  
플레이어 데이타라면 `player` 키워드를 `데이타`에 붙이면 됩니다. `player data`  
파일 데이타는 다른 데이타 종류와 다르게 플러그인이 비활성화되어도 저장되어 있습니다.  
게임 데이타는 게임 마다 서로 다른 저장소로 저장됩니다.  
플레이어 데이타는 게임 데이타 처럼 게임 마다 서로 다른 저장소로 저장되면서 플레이어마다 다르게 저장됩니다.

```
set data ( 이름 | 종원 )
print data ( 이름 )
```
```
* 위코드 실행했을 때 출력 매세지
종원
```
플레이어 데이타 키워드 `player`는 특별하게 생략할 수 있습니다.  
`이름` 이나 `종원` 같은 문자는 명령이 아니기 때문에 따옴표를 붙이지 않아도 됩니다.  
소괄호는 데이타 이름이나 데이타 값을 입력하기 위해 표시해야 합니다.  
`| 또는 &` 표시는 서로 다른 값이라고 표현하기 위한 구분 문자입니다.  
`set`은 데이타를 설정하는 키워드입니다.
```
set game data ( 이름 | 종원 )
print game data ( 이름 )
```
```
* 위코드 실행했을 때 출력 매세지
종원
```
```
set all data ( 이름 | 종원 )
print all data ( 이름 )
```
```
* 위코드 실행했을 때 출력 매세지
종원
```
`리스트, 아이템, 인벤토리, 블럭, 위치`도 `all`, `game`, `player`를 사용할 수 있습니다.

---

## 리스트

```
add list ( 목록 | 값1 )
set list ( 목록 | 0 | 값1 )
get list ( 목록 | 0 )
size list ( 목록 )
remove list ( 목록 | 값1 )
clear list ( 목록 )
```

---

## 위치

위치 이름이 `player` 키워드라면 플레이어의 위치로 합니다.

```
create location ( 스폰포인트 | world | 0 | 10 | 0 | 180 | 180 ) //월드, X, Y, Z, Yaw, Pitch
add location ( 스폰포인트 | 0 | 10 | 0 )
clone location ( player | 스폰포인트 )
contains location ( player | pos1 | pos2 )
exists location ( 스폰포인트 )
posX location ( player )
posY location ( player )
posZ location ( player )
posYaw location ( player )
posPitch location ( player )
remove location ( 스폰포인트 )
equals location ( 스폰포인트 | player )
```

---

## 아이템

```
set item ( 다야블럭 | code 57 )
name set item ( 다야블럭 | "&a아름다운블럭" )
set lore item ( 다야블럭 | 0 | "이 블럭은 아름답습니다." )
add lore item ( 다야블럭 | "이 블럭은 아름답습니다." )
exists item ( 다야블럭 )
remove item ( 다야블럭 )
```

---

## 인벤토리

인벤토리 이름이 `player` 키워드라면 플레이어의 인벤토리로 합니다.

```
create inventory ( menu | 54 | "메뉴 타이틀!" )
create inventory ( menu | HOPPER | "메뉴 타이틀!" )
add inventory ( menu | 다야블럭 )
set inventory ( menu | 0 | 다야블럭 )
clone inventory ( menu | menu2 )
size inventory ( menu )
type inventory ( menu )
exists inventory ( menu )
remove inventory ( menu )
clear inventory ( menu )
equals inventory ( menu | player )
open inventory ( menu )
close inventory
get item inventory ( menu | 0 | 메뉴아이템 )
```
---

## 블럭

블럭 데이타는 파일 데이타에는 없습니다.  
게임 데이타와 플레이어 데이타에만 있습니다.

```
set block ( 스폰블럭 | 스폰포인트 )
code block ( 스폰블럭 )
type block ( 스폰블럭 )
get location block ( 스폰블럭 | 블럭위치 )
```

---


## 조건문

```
if ( "첫번째값" = "두번째값" ) 
    print "참"
```
조건문은 조건에 따라 `코드`가 실행되는 `구문`입니다.
```
if ( 값1 = 값2 ) { 
    //참일 경우 실행된다.
} else {
    //거짓일 경우 실행된다.
}
```

`=` 등호는 `논리 연산자` 라고 부릅니다.  
`== 또는 =` 두 값이 같을 때 참.  
`!= 또는 /=` 두 값이 서로 다를 때 참.  
`<` 왼쪽 수가 오른쪽 수보다 작을 때 참.  
`>` 왼쪽 수가 오른쪽 수보다 클 때 참.  
`<=` 왼쪽 수가 오른족 수보다 작거나 같을 때 참.  
`>=` 왼쪽 수가 오른쪽 수보다 크거나 같을 때 참.

```
if ( 대한민국 /= 북한 ) { print "참." } else { print "거짓." }
```
```
* 위코드 실행했을 때 출력 매세지
참.
```
`if` 명령은 조건이 참일 때 다음 명령을 실행합니다.  
`else` 명령은 조건이 거짓일 때 다음 명령을 실행합니다.  
위 구문에서 `/=` 은 두 값이 서로 다를 때 참이므로 "참."이 출력되었습니다.  
만약 두 값이 같다면 두 값이 다르지 않아서 "거짓."이 출력될 것입니다.

```
if ( "첫번째값" = "두번째값" ) 
    if ( "세번째값" = "네번째값" ) 
        print 첫번째, 두번째값이 서로 같고, 세번째, 네번째값이 서로 같습니다
```
```
if ( "첫번째값" = "두번째값" & "세번째값" = "네번째값" )
    print 첫번째, 두번째값이 서로 같고, 세번째, 네번째값이 서로 같습니다
```
위 아래의 소스코드의 의미가 같습니다.  
`& 또는 &&` 앞 뒤에 조건이 모두 참일 때만 참입니다.  
`| 또는 ||` 앞 뒤에 조건중 하나라도 참일 때만 참입니다.

---

## 반복문

```
while ( 조건구문 ) {
    //조건이 참일 동안 여기에 있는 코드는 계속 실행됩니다.
}
```

```
set data ( i | 0 )
while ( data ( i ) < 10 ) {
    print data ( i ) 번째 실행 중입니다
    set data ( i | data ( i ) + 1 )
}
```

```
for ( 초기실행구문 | 조건구문 | 증감구문 ) {
    //실행 구문
}

//실행순서도: 
//0. 초기실행구문 
//1. 조건구문이 참이라면 2 를 실행하고 거짓이라면 5을 실행한다.
//2. 실행 구문
//3. 증감 구문
//4. 1 로 이동한다.
//5. 명령을 종료한다.
```

```
for ( set data ( i | 0 ) | data ( i ) < 10 | set data ( i | data ( i ) + 1 ) ) {
    print data ( i ) 번째 실행 중입니다
} 
```

---

## 명령

### Send message
`aliases: [ send, sendmessage, message, msg, print, say, sendmsg ]`

    print Hello  //플레이어에게 매세지를 보낸다
    game print Hello //게임에 참여해 있는 모든 플레이어에게 매세지를 보낸다
    all print Hello  //서버에 참여해 있는 모든 플레이어에게 매세지를 보낸다

### Broadcast
`aliases: broadcast, broadcastmessage, announce`

    broadcast Hello  //서버 전체에 매세지를 보낸다

### ActionBar
`aliases: sendactionbar, actionbar`

    actionbar Hello  //플레이어에게 액션바 매세지를 보낸다
    game actionbar Hello //게임에 참여해 있는 모든 플레이어에게 액션바 매세지를 보낸다
    all actionbar Hello  //서버에 참여해 있는 모든 플레이어에게 액션바 매세지를 보낸다

### Food

    food  //플레이어의 배고픔 수치를 출력한다
    set food 20  //플레이어의 배고픔을 설정한다
    add food 1  //플레이어의 배고픔을 증감시킨다

### Health

    health  //플레이어의 체력 수치를 출력한다
    set health 20  //플레이어의 체력을 설정한다
    add health 20  //플레이어의 체력을 증감시킨다

### GameMode

    gamemode  //플레이어의 게임 모드를 출력한다
    set gamemode  /플레이어의 게임모드를 설정한다 

### Name

    player name  //플레이어의 이름을 출력한다
    set player name testName  //플레이어의 표시이름을 설정한다
    set name tesetName  //플레이어의 탭 목룍 표시이름을 설정한다
    game name  //게임의 이름을 출력한다

### Permission

    permission ( op )  //플레이어가 오피가 있는지 여부를 출력한다
    permission ( freedyminigamemaker.admin )  
    /플레이어가 노드 권한을 갖고 있는지 여부를 출력한다

### Title

    <game 또는 all 또는 player> title ( 0 | 50 | 0 | "제목" | "부제목" )  
    //플레이어에게 페이드인 0 에, 지속시간 50, 페이드아웃 0으로 제목과 부제목을 보낸다  

### Sound

    <game 또는 all 또는 player> sound ( "minecraft:block.note.snare" | 1 | 1 )
    //플레이어에게 볼륨 1에 음높이 1로 소리를 재생합니다

    <game 또는 all 또는 player> sound ( "minecraft:block.note.snare" | -1 | 1 )
    //플레이어에게 위치에 따른 소리의 변화를 없애고 음높이 1로 소리를 재생합니다

### Uuid

    player uuid  //플레이어의 고유한 UUID를 출력합니다
    get random uuid  //무작위의 UUID를 출력합니다

### Timings

    timings print Hello  //다음 명령의 실행 시간을 밀리초로 출력합니다

### MilliSec
`aliases: millisec, millisecond, milliseconds`

    millisec  //1970 년 1 월 1 일 자정 부터 시작된 밀리초 타이머를 출력합니다

### Random

    random ( 0 | 100 )  //0 부터 100까지의 소수점이 있는 난수를 출력합니다

### Log

    log hello  //콘솔창에 매세지를 보냅니다

### Length

    length Hello  //매세지의 길이를 출력합니다

### Int

    int 3.14  //내림하여 소수점을 없애 출력합니다

### Split

    split ( "1,2,3" | "," | <game 또는 all 또는 player> listName )
    //첫번째 매세지를 두번째 매세지로 나눠서 리스트에 저장합니다

### Join

    join testGame  //플레이어를 게임에 참여시킵니다

### Left

    left  //플레이어가 플레이어 중인 게임에서 플레이어를 퇴장시킵니다

### Do

    do start  //start 명령번들을 실행합니다

### Refs

    refs ( testGame | bundleName )  
    //게임의 명령번들을 실행 중인 게임으로 실행합니다

### Async

    async print hello  //비동기로 명령을 실행합니다
    //비동기는 서버의 동작 흐름 외부에서 실행해서 명령 실행 시간이 길면 비동기를 사용합니다
    //하지만 비동기 실행은 다른 일반 실행과 흐름이 맞지 않아서
    //데이타를 공유하지 않는 것을 추천합니다

### Delay

    delay ( 20 ) print hello  //몇틱 후에 다음 구문을 실행 후 실행 코드를 출력합니다 (20틱은 1초)

    async delay ( 20 ) print hello  
    //몇틱 후에 다음 구문을 비동기로 실행 후 실행 코드를 출력합니다

### CancelTask

    cancel ( 실행코드 )  //실행을 대기 중이던 구문을 취소시킵니다

### Execute

    player execute 명령어  //플레이어가 명령어를 실행하게 합니다
    execute 명령어  //콘솔에서 명령어를 실행합니다
