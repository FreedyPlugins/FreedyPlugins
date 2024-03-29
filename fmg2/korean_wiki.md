
프리디 미니게임 메이커 2는 스크립트 형식의 미니게임 제작 플러그인입니다.  
명령을 실행하는 것이 기본 원리 입니다.

```
on move 
    print "당신은 움직였습니다!"
```
이딴 식으로 작동합니다.

```
on move {
    print("당신은 움직였습니다!")
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

## 이밴트 

### Join
플레이어가 서버에 입장했을 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| joinMessage | 데이타 | 입장 매세지 |

### Left
플레이어가 서버를 퇴장했을 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| leftMessage | 데이타 | 퇴장 매세지 |


### Pre game join
플레이어가 게임에 입장하기 전에

### Game join
플레이어가 게임을 입장했을 때

### Pre game left
플레이어가 게임을 퇴장하기 전에

### Game left
플레이어가 게임을 퇴장했을 때

### Pre game stop
플레이어가 없어서 미니게임이 비활성화되기 전에

### Game stop
플레이어가 없어서 미니게임이 비활성화될 때

### Interact
플레이어가 상호작용할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| interactAction | 데이타 | 클릭 종류 |
| interactHand | 데이타 | 손 종류 |
| interactBlockFace | 데이타 | 블럭 방향 |
| interactBlock | 블럭 | 클릭한 블럭 |
| interactItem | 아이템 | 클릭한 아이템 |

### Move
플레이어가 움직일 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| moveFrom | 위치 | 이전 위치 |
| moveTo | 위치 | 다음 위치 |

### Chat
플레이어가 채팅할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| chat | 데이타 | 채팅매세지 |

### Command
플레이어가 명령어를 실행할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| command | 데이타 | 입력한 명령어 |

### Inventory click
플레이어가 인벤토리를 클릭할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| inventoryClicked | 인벤토리 | 클릭한 인벤토리 |
| inventoryHotBar | 데이타 | 핫바 9칸 슬롯 |
| inventoryCursor | 아이템 | 손에 있던 아이템 |
| inventoryCurrentItem | 아이템 | 인벤토리에 있던 아이템 |
| inventoryAction | 데이타 | 클릭 종류 |
| inventoryClick | 데이타 | 클릭 종류 2 |
| inventoryRawSlot | 데이타 | 슬롯 위치 |
| inventorySlotType | 데이타 | 슬롯의 종류 |
| inventorySlot | 데이타 | 슬롯 위치 2 |

### Inventory drag
플레이어가 인벤토리를 드래그할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| inventoryDrag | 인벤토리 | 드래그한 인벤토리 |
| inventorySlots | 리스트 | 드래그한 슬롯들 |
| inventoryRawSlots | 리스트 | 드래그한 슬롯들 2 |
| inventoryDragItems | 리스트 | 넣어진 아이템 슬롯들 |
| inventoryDragItem_<slot> | 아이템 | 특정 슬롯의 넣어진 아이템 |
| inventoryCursor | 아이템 | 커서 아이템 |
| inventoryOldCursor | 아이템 | 이전 커서 아이템 |
| inventoryDragType | 데이타 | 드래그 종류 |


### Inventory close 
플레이어가 인벤토리를 닫을 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| inventoryClosed | 인벤토리 | 닫은 인벤토리 |

### Attack
플레이어가 엔티티를 공격할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| damage | 데이타 | 데미지 수치 |
| damageCause | 데이타 | 데미지 원인 |
| damageFinal | 데이타 | 최종적으로 계산된 수치 |
| entityUuid | 데이타 | 엔티티 UUID |

### Damage
플레이어가 엔티티에게 데미지를 입을 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| damage | 데이타 | 데미지 수치 |
| damageCause | 데이타 | 데미지 원인 |
| damageFinal | 데이타 | 최종적으로 계산된 수치 |
| attackerUuid | 데이타 | 플레이어 UUID |


### Player damage
플레이어가 데미지를 입을 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| damage | 데이타 | 데미지 수치 |
| damageCause | 데이타 | 데미지 원인 |
| damageFinal | 데이타 | 최종적으로 계산된 수치 |

### Drop item
플레이어가 아이템을 떨굴 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| dropItem | 아이템 | 떨군 아이템 |

### Teleport
플레이어가 텔레포트 할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| teleportFrom | 위치 | 이전 위치 |
| teleportTo | 위치 | 다음 위치 |

### Swap hand
플레이어가 F키로 오른손과 왼손을 맞바꿀 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| mainHandItem | 아이템 | 오른손 아이템 |
| offHandItem | 아이템 | 왼손 아이템 |

### Block break
플레이어가 블럭을 부쉈을 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| blockBreak | 블럭 | 부순 블럭 |

### Block place
플레이어가 블럭을 설치할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| blockPlace | 블럭 | 설치한 블럭 |

### Player respawn
플레이어가 리스폰할 때

| 이름 | 종류 | 설명 |
|--------------|--------------|--------------|
| respawnLocation | 위치 | 리스폰 위치 |

---

## 명령

### 데이타 수식어

    //데이타가 어디에 저장되는지를 표현하기 위한 수식어 입니다.
    //all 은 파일 단위 이고 영구적으로 저장됩니다   
    //game 은 게임 단위 이고 게임이 비활성화되면 소멸됩니다
    //player 는 플레이어 단위 이고 플레이어가 퇴장하면 소멸됩니다
    //대부분 이런 의미를 갖고 있지만 target의 수식어 all은 모두 확인하기 라는 의미를 가졌습니다


### 수학 연산

    cos 5  //각도의 삼각함수 코사인 값을 출력합니다
    sin 5  //각도의 삼각함수 사인 값을 출력합니다
    tan 5  //각도의 삼각함수 탄젠트 값을 출력합니다
    (1+1)  //두 값을 덧셈한 값을 출력합니다
    (1-1)  //두 값을 뺄셈한 값을 출력합니다
    (1*1)  //두 값을 곱셉한 값을 출력합니다
    (1/1)  //두 값을 나눗셈한 값을 출력합니다
    (1%1)  //두 값을 나눈 나머지 값을 출력합니다
    //2수를 초과해서 계산하려면 ((1+1)+1) 와 같이 해야 합니다 


### Data 
`aliases: [ data, var ]`

    data(some)  //어떤 데이타를 출력한다
    set data(some, Hello) //어떤 데이타를 설정한다

### List  

    add list(play, Hello)  //리스트에 매세지를 추가한다
    set list(play, 0, Hello)  //어떤 리스트에 0번 매세지를 설정한다
    clear list(play)  //리스트를 없앤다
    size list(play)  //리스트의 매세지 갯수를 출력한다
    contains list(play, Hello)  //리스트에 매세지가 있는지 여부를 출력한다
    remove list(play, Hello)  //리스트에 매세지를 삭제한다
    shuffle list(play)  //리스트를 섞는다
    clone list(play)  //리스트를 복제한다

### Location

    create location(spawn, world, 0, 0, 0)          //world 월드에 x좌표 0, y좌표 0, z좌표 0 위치를 저장합니다
    create location(spawn, world, 0, 0, 0, 90, 0)   //world 월드에 x좌표 0, y좌표 0, z좌표 0, yaw 90, pitch 0 위치를 저장합니다
    set posX location(spawn, 10)                    //위치의 X좌표를 설정합니다
    set posY location(spawn, 10)                    //위치의 Y좌표를 설정합니다
    set posZ location(spawn, 10)                    //위치의 Z좌표를 설정합니다
    set posYaw location(spawn, 10)                  //위치의 yaw를 설정합니다
    set posPitch location(spawn, 10)                //위치의 pitch를 설정합니다
    clone location(player, spawn)                   //위치를 다른 위치에 복제합니다
    add location(spawn, 0, 10, 0)                   //위치에 x좌표 0, y좌표 10, z좌표 0만큼 더합니다
    remove location(spawn)                          //위치를 삭제합니다
    exists location(spawn)                          //위치가 존재하는지 여부를 출력합니다
    equals location(spawn, player)                  //두 위치가 서로 같은지 여부를 출력합니다
    contains location(spawn, pos_A, pos_B)          //위치가 두 위치의 직사각형 안에 있는지 출력합니다
    get block(spawn, blockName)                     //위치에 있는 블럭을 저장합니다

### Block

    set block(blockName, spawnPoint)           //블럭 위치를 저장합니다
    remove block(blockName)                    //블럭을 삭제합니다
    get location block(blockName, spawnPoint)  //블럭 위치를 저장합니다
    set block(blockName, code 5, 1)            //블럭 코드를 5:1(가문비나무 판자) 로 설정합니다
    code block(blockName)                      //블럭 코드를 출력합니다

### Item 

    set item(itemName, code 35:5)            //코드 35:5(연두색 양털) 아이템을 저장합니다
    lore add item(itemName, "아이템 설명")     //아이템에 로어를 추가합니다
    lore set item(itemName, 0, "아이템 설명")  //아이템에 로어를 설정합니다
    name set item(itemName, "아이템 이름")     //아이템의 표시이름을 설정합니다
    exists item(itemName)                    //아이템이 존재하는지 여부를 출력합니다
    code item(itemName)                      //아이템 코드를 출력합니다
    equals item(itemName, targetItem)        //아이템이 같은지 요부를 출력합니다
    size item(itemName)                      //아이템의 갯수를 출력합니다
    size set item(itemName)                  //아이템의 갯수를 설정합니다

### Inventory

    create inventory(menu_1, 54, "메뉴 타이틀")      //몇칸짜리 인벤토리를 생성합니다
    create inventory(menu_1, HOPPER, "메뉴 타이틀")  //타입의 인벤토리를 생성합니다
    set inventory(menu_1, 0, itemName)             //인벤토리에 몇번째칸에 아이템을 설정합니다
    add inventory(menu_1, itemname )               //인벤토리에 아이템을 추가합니다
    open inventory(menu_1)                         //플레이어에게 인벤토리를 띄웁니다
    size inventory(menu_1)                         //인벤토리의 칸수를 출력합니다
    equals inventory(menu_1, player)               //두 인벤토리가 서로 같은지 여부를 출력합니다
    exists inventory(menu_1)                       //인벤토리가 존재하는지 여부를 출력합니다
    clear inventory(menu_1)                        //인벤토리에 아이템을 모두 삭제합니다
    clone inventory(menu_1, player)                //인벤토리를 다른 인벤토리에 복제합니다
    remove inventory(menu_1)                       //인벤토리를 삭제합니다
    close inventory                                //플레이어의 인벤토리를 닫습니다  
    get item inventory(player, hotbar, testItem)   //플레이어가 들고 있는 아이템의 슬롯을 아이템에 저장합니다 
    //구글에 InventoryType <서버버전> spigot 이라고 치면 모든 인벤토리 종류를 찾을 수 있습니다

### Target

    name target(Notch) set helath 20  //어떤 이름으로 된 플레이어로 다음 명령을 실행합니다
    target(player uuid) set food 20   //UUID로 된 플레이어로 다음 명령을 실행합니다
    all target(play) {         //플레이어 이름 또는 플레이어 UUID로 이루어진 리스트로 플레이어를 찾고 한번씩 모두 다 다음 명령을 실행합니다
        add food -1
    }                                 
    get list target(testList, eachMessage) {
        print game data(eachMessage)  //리스트에 매세지를 한번씩 모두 다 다음 명령을 실행합니다
    }                                 

### Send message
`aliases: [ send, sendmessage, message, msg, print, say, sendmsg ]`

    print Hello      //플레이어에게 매세지를 보낸다
    game print Hello //게임에 참여해 있는 모든 플레이어에게 매세지를 보낸다
    all print Hello  //서버에 참여해 있는 모든 플레이어에게 매세지를 보낸다

### Broadcast
`aliases: broadcast, broadcastmessage, announce`

    broadcast Hello  //서버 전체에 매세지를 보낸다

### ActionBar
`aliases: sendactionbar, actionbar`

    actionbar Hello      //플레이어에게 액션바 매세지를 보낸다
    game actionbar Hello //게임에 참여해 있는 모든 플레이어에게 액션바 매세지를 보낸다
    all actionbar Hello  //서버에 참여해 있는 모든 플레이어에게 액션바 매세지를 보낸다

### BossBar

    create bossbar(testBossBar, WHITE)     //어떤 색깔에 보스바를 생성합니다
    open bossbar(testBossBar)              //플레이어에게 보스바를 엽니다
    close bossbar(testBossBar)             //플레이어의 보스바를 닫습니다
    remove bossbar(testBossBar)            //보스바를 삭제합니다
    set size bossbar(testBossBar, 1)       //보스바의 프로세스바를 0부터 1안에 숫자로 설정합니다
    set type bossbar(testBossBar, SOLID)   //보스바에 스타일을 설정합니다
    set color bossbar(testBossBar, WHITE)  //보스바에 색깔을 설정합니다
    exists bossbar (testBossBar)           //보스바가 존재하는지 여부를 출력합니다
    //가능한 색깔: PINK, BLUE, RED, GREEN, YELLOW, PURPLE, WHITE
    //가능한 스타일: SOLID, 6, 10, 12, 20 또는 쓰지 않기

### Food

    food         //플레이어의 배고픔 수치를 출력한다
    set food 20  //플레이어의 배고픔을 설정한다
    add food 1   //플레이어의 배고픔을 증감시킨다

### Health

    health         //플레이어의 체력 수치를 출력한다
    set health 20  //플레이어의 체력을 설정한다
    add health 20  //플레이어의 체력을 증감시킨다

### GameMode

    gamemode      //플레이어의 게임 모드를 출력한다
    set gamemode  //플레이어의 게임모드를 설정한다 

### Name

    player name               //플레이어의 이름을 출력한다
    set player name testName  //플레이어의 표시이름을 설정한다
    set name tesetName        //플레이어의 탭 목룍 표시이름을 설정한다
    game name                 //게임의 이름을 출력한다

### Permission

    permission(op)  //플레이어가 오피가 있는지 여부를 출력한다
    permission(freedyminigamemaker.admin)  
    //플레이어가 노드 권한을 갖고 있는지 여부를 출력한다

### Title

    title(0, 50, 0, "제목", "부제목")  
    //플레이어에게 페이드인 0 에, 지속시간 50, 페이드아웃 0으로 제목과 부제목을 보낸다  

### Sound

    sound("minecraft:block.note.snare", 1, 1)
    //플레이어에게 볼륨 1에 음높이 1로 소리를 재생합니다

    sound("minecraft:block.note.snare", -1, 1)
    //플레이어에게 위치에 따른 소리의 변화를 없애고 음높이 1로 소리를 재생합니다

### Particle 

    particle(player, FLAME, 10, true)  //위치에 파티클 효과 10개를 멈춰있는 상태로 소환합니다
    particle(player, FLAME, 10)        //위치에 파티클 효과 10개를 소환합니다
    //구글에 Particle <서버버전> spigot 이라고 치면 모든 파티클 효과를 찾을 수 있습니다


### Potion

    add potion(GLOWING, 55555, 0)  //레벨 1의 포션효과를 지속시간 동안 줍니다 (포션 1레벨은 0입니다)    
    remove potion(GLOWING)         //포션효과를 제거합니다
    clear potion                   //포션효과를 모두 제거합니다
    //구글에 PottionEffectType <서버버전> spigot 이라고 치면 모든 포션을 찾을 수 있습니다

### HotBar

    get hotbar  //플레이어의 핫바 슬롯을 출력합니다
    set hotbar  //플레이어의 핫바 슬롯을 설정합니다

### Sneaking
`aliases: [ sneaking, sneak ]`

    sneaking  //플레이어가 웅크리고 있는지 여부를 출력합니다

### Velocity

    set velocity(0, 10, 0)  // Y 좌표 10 만큼 추진력을 설정합니다
    add velocity(0, 10, 0)  // Y 좌표 10 만큼 추진력을 더합니다 

### Uuid

    player uuid      //플레이어의 고유한 UUID를 출력합니다
    get random uuid  //무작위의 UUID를 출력합니다

### Timings

    timings print Hello  //다음 명령의 실행 시간을 밀리초로 출력합니다

### MilliSec
`aliases: millisec, millisecond, milliseconds`

    millisec  //1970 년 1 월 1 일 자정 부터 시작된 밀리초 타이머를 출력합니다

### Random

    random(0, 100)  //0 부터 100까지의 소수점이 있는 난수를 출력합니다

### Log

    log hello  //콘솔창에 매세지를 보냅니다

### Length

    length Hello  //매세지의 길이를 출력합니다

### Int

    int 3.14  //내림하여 소수점을 없애 출력합니다

### Split

    split("1,2,3", ",", listName)
    //첫번째 매세지를 두번째 매세지로 나눠서 리스트에 저장합니다

### Join

    join testGame  //플레이어를 게임에 참여시킵니다

### Left

    left  //플레이어가 플레이어 중인 게임에서 플레이어를 퇴장시킵니다

### Do

    do start  //start 명령번들을 실행합니다

### Return

    return false  //매세지를 번들이나 이밴트에게 전달하고 명령을 중단합니다 
    //예를 들어서, interact 이밴트에서 실행되면 상호작용이 취소됩니다

### Refs

    refs(testGame, bundleName)  
    //게임의 명령번들을 실행 중인 게임으로 실행합니다

### Async

    async print hello  //비동기로 명령을 실행합니다
    //비동기는 서버의 동작 흐름 외부에서 실행해서 명령 실행 시간이 길면 비동기를 사용합니다
    //하지만 비동기 실행은 다른 일반 실행과 흐름이 맞지 않아서
    //데이타를 공유하지 않는 것을 추천합니다

### Delay

    delay(20) print hello  //몇틱 후에 다음 구문을 실행 후 실행 코드를 출력합니다 (20틱은 1초)

    async delay(20) print hello  
    //몇틱 후에 다음 구문을 비동기로 실행 후 실행 코드를 출력합니다

### TaskId

    taskId  //실행되는 코드가 Delay 명령으로 실행되었다면, 실행 코드를 출력합니다

### CancelTask

    cancel (실행 코드)  //실행을 대기 중이던 구문을 취소시킵니다

### Execute

    player execute 명령어  //플레이어가 명령어를 실행하게 합니다
    execute 명령어  //콘솔에서 명령어를 실행합니다

## 조건문

```
if ("첫번째값" = "두번째값") 
    print "참"
```
조건문은 조건에 따라 `코드`가 실행되는 `구문`입니다.
```
if (값1 = 값2) { 
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
if (대한민국 /= 북한) {print "참."} else {print "거짓."}
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
if("첫번째값" = "두번째값") 
    if("세번째값" = "네번째값") 
        print 첫번째, 두번째값이 서로 같고, 세번째, 네번째값이 서로 같습니다
```
```
if("첫번째값" = "두번째값" & "세번째값" = "네번째값")
    print 첫번째, 두번째값이 서로 같고, 세번째, 네번째값이 서로 같습니다
```
위 아래의 소스코드의 의미가 같습니다.  
`& 또는 &&` 앞 뒤에 조건이 모두 참일 때만 참입니다.  
`| 또는 ||` 앞 뒤에 조건중 하나라도 참일 때만 참입니다.

---

## 반복문

```
while(조건구문) {
    //조건이 참일 동안 여기에 있는 코드는 계속 실행됩니다.
}
```

```
set data(i, 0)
while(data(i)<10) {
    print data(i) 번째 실행 중입니다
    set data(i, data(i)+1)
}
```

```
for (초기실행구문, 조건구문, 증감구문) {
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
for (set data(i,0) | data(i)<10 | set data(i,data(i)+1)) {
    print data(i) 번째 실행 중입니다
} 
```

---
