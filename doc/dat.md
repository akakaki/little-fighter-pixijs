# 文件解析

## 角色(charactor)

◎基本介紹◎

<BMP_BEGIN>

name: Davis人名

head: sprite\sys\davis_f.bmp大頭照位置

small: sprite\sys\davis_s.bmp能量棒人照位置

file(0-69): sprite\sys\davis_0.bmp w: 79 h: 79 row: 10 col: 7

file(70-139): sprite\sys\davis_1.bmp w: 79 h: 79 row: 10 col: 7

file(140-209): sprite\sys\davis_2.bmp w: 79 h: 79 row: 10 col: 7

w: 79--->每一格的寬度

h: 79--->每一格的高度

row: 10 col: 7 那一張圖總共有幾行幾列

row: 10共有幾行

col: 7共有幾列

walking_frame_rate :走路的動作變換的時間(值愈大，則愈慢)

walking_speed :移動速度

walking_speedz :行時斜移動的速度

running_frame_rate :跑步的動作變換的時間

running_speed :跑速度

running_speedz :跑時斜移動的速度

heavy_walking_speed :拿重物的移動速度

heavy_walking_speedz:拿重物時斜移動的速度

heavy_running_speed :拿重物的跑速度

heavy_running_speedz:拿重物時斜跑的速度

jump_height :跳的高度

jump_distance :跳的距離

jump_distancez :跳時斜跳的距離

dash_height :衝跳的高度

dash_distance :衝跳的距離

dash_distancez :衝跳時斜衝跳的距離

rowing_height 受身時向上的高度(負值)

rowing_distance 受身時向後的速度

<BMP_END>





<特別發現>

強化網頁的強化版是如何鎖碼的？僅是在人名之前加上中文字而已。寫入中文字

會導致編輯器讀不到檔案(並非所有的字都會)，因此就像鎖碼一樣。鎖碼的話會

造成自己也無法改，除非你有另存未鎖碼的，不然以後你也不能再修改了。

破解方法(會破解的人應該不多才對！)：故意先讓lf2.exe執行時人物的dat檔出

錯(可以先將其中一張圖移開讓它圖取不到)，它會告訴你出錯並終止。然後再去

看data資料夾中的temporary.txt，它顯示出的就是這個錯誤的dat檔的內容。







◎人物act(即frame)的分布◎



0 ~ 3: standing (站立)

5 ~ 8: walking (行走)

9 ~ 11: running (跑步)

12 ~ 15: heavy_obj_walk (拿重物時走路)

16 ~ 18: heavy_obj_run (拿重物時跑步)

19: heavy_stop_run (拿重物時煞車)

20 ~ 23: normal_weapon_atck (拿輕物時攻擊)

25 ~ 28: normal_weapon_atck (同前，分成兩個動作)

30 ~ 33: jump_weapon_atck (拿輕物時跳攻擊)

35 ~ 37: run_weapon_atck (拿輕物時跑攻擊)

40 ~ 43: dash_weapon_atck (拿輕物時跑跳攻擊)

45 ~ 47: light_weapon_thw (丟出輕物)

50 ~ 51: heavy_weapon_thw (丟出重物)

52 ~ 54: sky_lgt_wp_thw (跳時丟出輕物)

55 ~ 58: weapon_drink (喝可以喝的道具)

60 ~ 62: punch (普通攻擊)

65 ~ 67: punch (同前，分成兩個動作)

70 ~ 75: super_punch (重擊)

80 ~ 81: jump_attack (跳攻擊)

85 ~ 87: run_attack (跑攻擊)

90 ~ 91: dash_attack (跑跳攻擊)

95: dash_defend (跑跳防禦) ←有這個動作嗎？？？

100 ~ 101: rowing (向後授身)

103 ~ 107: rowing (迴避、滾地)

108 ~ 109: rowing (向前授身)

110: defend (防禦)

111: defend (防禦時被打到)

112 ~ 114: broken_defend (破擋，即檔不住時的動作)

115 ~ 116: picking_light (撿起輕物)

117: picking_heavy (撿起重物)

120 ~ 123: catching (捉住人時的動作)

130 ~ 144: picked_caught (被捉，其中有一些是被捉時被打的動作)

180 ~ 185: falling (向前跌倒)

186 ~ 191: falling (向後跌倒)

200 ~ 202: ice (被冰封)

203 ~ 206: fire (被火燒)

207: tired (累，但不是暈眩) ←有這個動作嗎？？？

210 ~ 212: jump (跳躍)

213 ~ 214: dash (跑跳)

215: crouch (爬起)

218: stop_running (煞車)

219: crouch2 (第二個爬起的動作)

220 ~ 221: injured (被打到向後退的動作)

222 ~ 223: injured (被打到向前移的動作)

224 ~ 229: injured (暈眩)

230: lying (躺著的倒地，死亡時會自動不斷的重複此動作)

231: lying (趴著的倒地，死亡時會自動不斷的重複此動作)

232 ~ 234: throw_lying_man (摔出被捉住的人)

399: dummy (人物模型) ←不可刪除，且為人物frame數的上限



※235~398之間的frame就是絕技的動作，是可以任意命名及改變的。

※有些frame的數量因人而異，例如Bandit的punch是60~61 & 65~66，但Davis是

60~63 & 65~68。





◎frame解說◎



<FRAME>=動作開始



72 super_punch=號碼和名



pic: 8 =圖檔位置(從0開始算)



state:

0=站立(stand)

1=行走(walk)

2=跑步(run)

3=普通拳腳攻擊(punch)

4=跳(jump)

5=突進(dash，即跑+跳)

7=擋(defend)

8=破擋(broken defend)

9=捉人(catching)

10=被捉(picked caught)

11=被攻擊(injured)

12=fall大於60才會被打到

13=可被同盟攻擊，且有冰碎效果

14=倒在地上(lying)可使com不會追你

15=被冰封(ice)

16=暈眩(tired)可被敵人捉住

17=喝(weapon drink)可以喝的物件被消耗

18=燃燒(fire，可攻擊我方同盟)

19=firen的烈火焚身(burn run)

301=deep的鬼哭斬(dash sword，此state具有人物上下移動的功能)

400=woody瞬間轉移(teleport，移往最近的敵人)

401=woody瞬間轉移(teleport，移往最近的隊友)

500=rudolf轉換成其他角色(transform)

501=rudolf轉換回來(transform_b)

1700=治療自己

9995=變身成LouisEX(transform，任何人都可以)

9996=爆出盔甲(transform，任何人都可以)

9997=訊息(come,move之類，能在任何地方看見)

9998=掉到地面上才會消失

9999=毀壞的武器(broken weapon)



<特別說明>18會有冒煙效果，但此state的攻擊會傷及我方。





wait: 2 =停頓時間



next: 73 =下一個動作是



dvx: =向前後行多少

dvy: =向天,地行多少

dvz: =向上下行多少



centerx: 是以哪一點作為人物的中央

centery: 是以哪一點作為人物的底部(腳的位置)



hit_a: 按攻擊時,跳到哪一個frame?

hit_d: 按防衛時,跳到哪一個frame?

hit_j: 按跳時,跳到哪一個frame?

hit_Ua: 按D^A時,跳到哪一個frame?

hit_Fj: 按D>J時,跳到哪一個frame?

hit_Da: 按DvA時,跳到哪一個frame?

以此類推...





<特別說明>

1.next:0是不斷重複此動作，hit_?:的0是指沒有設定。

2.next、hit_? :999是指回到隨機動作

3.next、hit_? :1000是消失

4.next:1280=rudolf的隱形

(使用隱身和變化術也會影響到分身)

5.next: -??? 會反向進行第???個frame



<特別發現>next:1200~1299是隱形





◎itr解說◎



itr: =身體攻擊動作開始



kind:

0=特殊特技

1=捉住暈眩(state:16)的人

2=撿武器

3=強迫抓人

6=敵人靠近按A時是重擊

7=撿武器不影響動作

8=injury數值變成治療多少hp，動作跳至dvx:?

9=打中敵人自己hp歸0(如John的防護罩)

10=henry魔王之樂章效果

14=阻擋

15=飛起

16=結冰

1???=被你打到會跳到第??個frame(如人質的kind)



x: 40 ,w: 35=攻擊前~後的距離 y: 5 ,h: 45 攻擊上~下的距離



dvx:3 =打中會往後彈後多遠

dvy:-10 =打中會彈多高(負值是向天空，正值是向地面)



fall: 70 =倒下的機會

fall0是敵人只動一下

fall30是打兩下敵人就暈

fall40是打一下往後退打第二下就倒地

fall60是打一下暈眩打第二下就倒地

fall70是必定倒地



vrest:15 =同一個frame打到人的中間間隔時間(vrest越小，同一個frame就會打

到越多下)。如Davis的昇龍霸，原本vrest只有10，若改的更低，則

會造成如強化網頁的神龍拳的連擊效果。

※注意：vrest值最低只能是4，更低的話打到人會卡住。



arest: (vrest無效)一攻擊到一個人，多久後才能再打一個人





bdefend: 60 =破擋的機會(即打破敵人防禦的機會)

bdefend: 60打一次就破擋；同fall，如值是16則16+16+16+16大於60所以值是16

時打敵人4下就破擋。

bdefend: 100則完全擋不住，就算按擋也會讓你直接被打到，連破擋的動作都跳

過。且有防禦效果的人物(如Julian.Knight.Louis)也防不住；道具也

會直接被毀掉(不論道具的HP有多少)。



injury: 40 =殺傷力(即損害敵人hp多少；玩家的hp是預設值的500)



在injury後面加上以下effect會有特效(僅限於kind:0時有作用)

effect: 0 拳擊

effect: 1 利器攻擊

effect: 2 著火

effect: 3 結冰

effect: 4 穿過敵人(僅能打中type:1.2.3.4.5.6的物件)

effect: 5 (或以上)沒效果，也打不中任何東西

effect: 20 定身火(此effect可以避免state:18的攻擊波及我方)

effect: 21 著火(此effect可以避免state:18的攻擊波及我方)

effect: 22 著火(此effect可以避免state:18的攻擊波及我方)

effect: 30 定身冰



effect可以加上負號(有效果但無聲音)。

若要加大攻擊的z軸範圍,只要在effect或injury的後面加上zwidth: ??即可

(沒有effect就是加在injury的後面,若有effect則加在effect的後面)



itr_end: =身體攻擊動作結束





<特別說明>大範圍攻擊→

itr:

kind: 0 x: -x y: -x w: x h: x dvx: ? dvy: ? fall: ? vrest: ?

bdefend: ? injury: ? zwidth: x effect: ?

itr_end:



x數值越高則範圍越大，?數值是看自己高興填寫的。





◎bdy解說◎



bdy: =身體(受攻擊的部分)開始



kind: 0 特殊特技



x: 26 w: 35 =受攻擊前~後的距離 y: 12 h: 66=受攻擊上~下的距離



bdy_end:=身體結束



<FRAME_END>= 動作結束



若要消耗mp只要在<FRAME>之後的第一行結尾加上mp: ?? 即可。

※若mp為1000以上則會變成扣hp，如firen的大轟炸是4300，就會扣40點hp及300

點的mp



聲音：只要再第一行與第二行之間插入sound: data/???.wav即可





◎opoint解說◎



若要在某個動作加入發出氣功波類型的絕技，只要在frame裏加入以下即可：

opoint:

kind: ? x: ? y: ? action: ? dvx: ? dvy: ? oid: ? facing: ?

opoint_end:



opoint: objectpoint開始



kind: 1=發出氣功波



x:發出的氣功的前後位置

y:發出的氣功的天地位置



action: 招式的第幾個frame



dvx:向前後飛行的速度

dvy:向天地飛行的速度



oid:氣功波的id(請參考data/data.txt)



facing:數量及正反 (如數量是1個,正向→facing: 0；2個,正向→facing:20 ；

1個,反向→facing:1 ； 2個,反向→facing: 21)

前面數字是數量，數量若為1則不須填，但2以上就須填了；後面數字為正反向，

偶數是正向，奇數是反向。



opoint_end: objectpoint結束





◎wpoint解說◎



若frame中有wpoint如下：



wpoint:

kind: ? x: ? y: ? weaponact: ? attacking: ? cover: ? dvx: ? dvy: ?

dvz: ?

wpoint_end:



wpoint:是指此動作若拿著武器時則武器會是哪一個。



x.y:武器的位置座標



weaponact:武器的第幾個frame



attacking:此時武器有否攻擊性(0是無攻擊，1是站著時的攻擊，2是跳時的攻擊

，3是衝時的攻擊，4是衝跳時的攻擊)



cover: 0是你會蓋住武器的圖示 1是武器會蓋住你的圖示



dvx.dvy.dvz:武器會往x.y.z座標移動多少



wpoint_end: weaponpoint結束





◎bpoint解說◎



bpoint:

x: 43 y: 38

bpoint_end:



bpoint: 流血指令開始



x: y: 嘴角的位置



bpoint_end: 流血指令結束



※hp少於1/3時，嘴角才會流血。





◎抓人◎



若要抓起敵人,則要在itr中寫入

itr:

kind: ? x: ? y: ? w: ? h: ? vrest: ?

catchingact: ??? ??? caughtact: ??? ???

itr_end:



caughtingact: 指抓住敵人後自己跳到第幾個frame(需重複寫兩次)

caughtact: 指抓住敵人後敵人跳到第幾個frame





或者在cpoint中寫入



cpoint:

kind: ? x: ? y: ? vaction: ? aaction: ? taction: ?

injury: ? hurtable: ? decrease: ? throwvx: ? throwvy: ?

throwvz: ? throwinjury: ?

另外有fronthurtact: ? backhurtact: ? dircontrol: ?

cpoint_end:





cpoint: 抓人指令開始

kind: 抓人狀態，1是抓人，2是被抓的(必須配合，1抓2的，否則抓不起來)

x: x座標，與被抓的x座標配合

y: y座標，與被抓的y座標配合

vaction: 敵人的act

aaction: 按A時自己跳到的act

taction: 按→A時自己跳到的act

injury: 被抓的敵人受傷量(正值是受傷+停格，負值是受傷不停格)

hurtable: 敵人會不會被人打到？(0不會，1會)※但vaction:在133 ~ 144的敵

人不會被打到

decrease: (負值)抓住的時間減少值(總抓住的時間值301/?=抓住的時間)

throwvx: 丟出去的x速度

throwvy: 丟出去的y速度

throwvz: 丟出去的z速度(要按↑↓才會丟斜的)

throwinjury: 被丟者的受傷量

※-842150451不知是什麼…

fronthurtact: (正面被打後的act)

backhurtact: (背面被打後的act)

dircontrol: 控制方向(按著→進入此動作會向右轉，負數則會相反)

cpoint_end: 抓人指令結束



throwinjury完全說明

※throwvx: 不能為0，否則自己會消失。-1是變成被抓者的id(樣子)如Rudolf，

之後可按DJA變回來，若想再變回去則只能用state: 501

可惜的是會無法使用按DJA會使出的招式(會變回來)





◎關於變身◎



在state的地方寫成8???(←???是要寫入人物的id)

並且在要變成的那個人的圖檔位置做以下的改變：



角色有一個圖檔時：

<BMP_BEGIN>

name: xxx

head: sprite\sys\xxx_f.bmp

small: sprite\sys\xxx_s.bmp

file(0-69): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(70-139): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(140-209): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7



角色有兩個圖檔時：

<BMP_BEGIN>

name: xxx

head: sprite\sys\xxx_f.bmp

small: sprite\sys\xxx_s.bmp

file(0-69): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(70-139): sprite\sys\xxx_1.bmp w: 79 h: 79 row: 10 col: 7

file(140-209): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(210-279): sprite\sys\xxx_1.bmp w: 79 h: 79 row: 10 col: 7



角色有三個圖檔時：

<BMP_BEGIN>

name: xxx

head: sprite\sys\xxx_f.bmp

small: sprite\sys\xxx_s.bmp

file(0-69): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(70-139): sprite\sys\xxx_1.bmp w: 79 h: 79 row: 10 col: 7

file(140-209): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(210-279): sprite\sys\xxx_1.bmp w: 79 h: 79 row: 10 col: 7

file(280-349): sprite\sys\xxx_2.bmp w: 79 h: 79 row: 10 col: 7

file(350-419): sprite\sys\xxx_2.bmp w: 79 h: 79 row: 10 col: 7

file(420-489): sprite\sys\xxx_2.bmp w: 79 h: 79 row: 10 col: 7



角色有四個圖檔時：

<BMP_BEGIN>

name: xxx

head: sprite\sys\xxx_f.bmp

small: sprite\sys\xxx_s.bmp

file(0-69): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(70-139): sprite\sys\xxx_1.bmp w: 79 h: 79 row: 10 col: 7

file(140-209): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(210-279): sprite\sys\xxx_1.bmp w: 79 h: 79 row: 10 col: 7

file(280-349): sprite\sys\xxx_2.bmp w: 79 h: 79 row: 10 col: 7

file(350-419): sprite\sys\xxx_3.bmp w: 79 h: 79 row: 10 col: 7

file(420-489): sprite\sys\xxx_2.bmp w: 79 h: 79 row: 10 col: 7

file(490-559): sprite\sys\xxx_3.bmp w: 79 h: 79 row: 10 col: 7



角色有五個圖檔時：

<BMP_BEGIN>

name: xxx

head: sprite\sys\xxx_f.bmp

small: sprite\sys\xxx_s.bmp

file(0-69): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(70-139): sprite\sys\xxx_1.bmp w: 79 h: 79 row: 10 col: 7

file(140-209): sprite\sys\xxx_0.bmp w: 79 h: 79 row: 10 col: 7

file(210-279): sprite\sys\xxx_1.bmp w: 79 h: 79 row: 10 col: 7

file(280-349): sprite\sys\xxx_2.bmp w: 79 h: 79 row: 10 col: 7

file(350-419): sprite\sys\xxx_3.bmp w: 79 h: 79 row: 10 col: 7

file(420-489): sprite\sys\xxx_2.bmp w: 79 h: 79 row: 10 col: 7

file(490-559): sprite\sys\xxx_3.bmp w: 79 h: 79 row: 10 col: 7

file(560-629): sprite\sys\xxx_4.bmp w: 79 h: 79 row: 10 col: 7

file(630-699): sprite\sys\xxx_4.bmp w: 79 h: 79 row: 10 col: 7

file(700-769): sprite\sys\xxx_4.bmp w: 79 h: 79 row: 10 col: 7



以此類推............



※注意：若需作此改變，則不管你的bmp檔有幾個圖你都要寫成70張圖的設定值。

如:Bat_2.bmp這個圖檔僅有二張圖，但設定值必須改成file(280-349)、row:10、

col:7這樣，否則會沒有顯示圖檔。

圖檔最多不能超出500個。



------------氣功波型(即發射出去的)絕技介紹--------------



◎基本解說◎



<BMP_BEGIN>

file(0-23): sprite\sys\dennis_chase.bmp w: 81 h: 82 row: 4 col: 3

weapon_hit_sound: data\020.wav

weapon_drop_sound: data\020.wav

weapon_broken_sound: data\020.wav

<BMP_END>





file:圖檔所在,同上面所介紹的



weapon_hit_sound: 打中人的聲音

weapon_drop_sound: 撞到地上的聲音

weapon_broken_sound: 毀壞聲音





<FRAME>0 flying

pic: 0 state: 3000 wait: 2 next: 40 dvx: 3 dvy: 0 dvz: 0 centerx: 45

centery: 38 hit_a: 0 hit_d: 0 hit_j: 0

itr:

kind: 0 x: 28 y: 30 w: 27 h: 26 dvx: 18 fall: 70 vrest: 15 bdefend: 60

injury: 65

itr_end:

bdy:

kind: 0 x: 28 y: 30 w: 27 h: 26

bdy_end:

<FRAME_END>





◎設定解說◎



此時的 hit_a: 0 hit_d: 0 hit_j: 0是指特殊設定



一般而言，

hit_a: 時間減少量，(時間總值500/hit_a=持續時間)，數值越低減少越慢

hit_d: 當時間總值扣完時動作跳到此

hit_j: z方向移動速度，50為中間，49以下是上移的速度，51以上是下移的速度

hit_Fa: 追縱的程度，說明如下：

1= 追敵人的center(因為敵人站在地面，所以會下飄)

2= 水平追敵

3= 加速法追敵(追縱力較差)

4= 天使之祝福(別的dat檔用了無效)

5= 天使之祝福的開始(會追我方的人物很久)

6= 惡魔之審判的開始(視敵人數目而增加，基本上是一個)

7= 惡魔之審判,殃殞天降(可以做出打到地面的追蹤波)

8= 吸血蝙蝠的開始(視敵人數目而增加，基本數值是三個，別的dat檔用了無效)

9= 殃殞天降的開始(視敵人數目而增加，基本數值是四個)

10= 加速(從慢變快)

11= 極地火山

12= 吸血蝙蝠

13= 連環重炮的開始

14= 連環重炮





※當hit_a的時間到後，hit_Fa就會失去效用。

※追蹤功能類型的氣功波dvx.dvy.dvz必須是0。





氣功波state使用



15= 若配合沒有bdy則永遠不會被打消

18= 氣功會冒煙，且會波及我方。但若配上effect:22則可以避免此效果。

3000="波"的飛行(ball-flying，波是指氣功波)，打到人和自己的武器會跳到

act10，打到別人的武器跳到act20

3001="波"打中敵時的爆破(hiting)，打到人和自己的武器不消失，正面打到別

人的武器act20

3002=波被取消，即被其他東西打中阻擋而爆破(hit)，打到人和自已的武器不消

失，打到別人type1的武器act20

3003=波的反彈及爆破(rebounding)，打到人和type2的武器不消失，打到別人的

武器act20

3004=波消失(disappear)，打到人和type2.4.6的武器不消失，打到type1的武器

act20

3005="拳氣"的飛行(henry wind-flying)，打到東西不消失，打到state3005的

act20，無法上下移動，沒有影子

3006=屬穿心攻擊的波(flying)，打到東西不消失，打到state3005.3006的act20





◎氣功act分布◎

10: hitting (打中敵人)

20: hit (氣功波本身被打中)

30: rebounding (被反彈)

40: disappearing (消失)


## 道具(prop)

◎type:1,4,6的輕型武器◎



weapon_hp: 武器的hp量

weapon_drop_hurt: 武器著地的損血量

weapon_hit_sound: 被打到的聲音

weapon_drop_sound: 掉到地上的聲音

weapon_broken_sound: 毀壞的聲音



<WEAPON_STRENGTH_LIST>(武器攻擊表開始)

entry: 1 normal

dvx: 2 fall: 40 vrest: 10 bdefend: 16 injury: 30 effect: 3

entry: 2 jump

dvx: 7 fall: 70 vrest: 10 bdefend: 16 injury: 30 effect: 3

entry: 3 run

dvx: 10 fall: 70 vrest: 10 bdefend: 16 injury: 40 effect: 3

entry: 4 dash

dvx: 12 fall: 70 vrest: 20 bdefend: 60 injury: 40 effect: 3

<WEAPON_STRENGTH_LIST_END>(武器攻擊表結束)



在人物的wpoint的attacking使用哪個數字，就會用該entry的攻擊方式

※可以自己新增entry: 5以上的數字，不過人物的attacking就要用5





◎輕型道具act的分布◎

0: in_the_sky (在空中)

20: on_hand (在手中)

40: throwing (丟出)

60: on_ground (在地上)

64: 可以撿的on_ground

70: just_on_ground (剛掉到地上的動作)



state說明

1000=輕型武器在空中(light weapon-in the sky)

1001=輕型武器在手中(on hand)，類似arest:1

1002=輕型武器被投擲(throwing)，重力變弱，打到人act5,10,15

1003=輕型武器反彈(rebounding)

1004=輕型武器在地上(on ground)，與itr kind2作用





◎type 2重型武器◎



大部分與其他weapon相同，僅act.state不同





◎重型道具act分布◎

0: in_the_sky

10: on_hand

20: 可以撿的on_ground



state說明

2000= 重型武器在空中(heavy weapon-...同輕型道具)

2001= 重型武器在手中

2002= 重型武器在地上

2004= 與itr kind2作用





-------------新增人物、道具、武器、背景方法--------------



id: 0 type: 0 file:data\template.dat =Template

id: 52 type: 0 file:data\julian.dat =Julian

id: 51 type: 0 file:data\firzen.dat =Firzin

id: 50 type: 0 file:data\louisEX.dat =LouisEX

id: 38 type: 0 file:data\bat.dat =Bat

id: 39 type: 0 file:data\justin.dat =Justin

id: 37 type: 0 file:data\knight.dat =Knight

id: 36 type: 0 file:data\jan.dat =Jan

id: 35 type: 0 file:data\monk.dat =Monk

id: 34 type: 0 file:data\sorcerer.dat =Sorcerer

id: 33 type: 0 file:data\jack.dat =Jack

id: 32 type: 0 file:data\mark.dat =Mark

id: 31 type: 0 file:data\hunter.dat =Hunter

id: 30 type: 0 file:data\bandit.dat =Bandit

id: 1 type: 0 file:data\deep.dat =Deep

id: 2 type: 0 file:data\john.dat =John

id: 4 type: 0 file:data\henry.dat =Henry

id: 5 type: 0 file:data\rudolf.dat =Rudolf

id: 6 type: 0 file:data\louis.dat =Louis

id: 7 type: 0 file:data\firen.dat =Firen

id: 8 type: 0 file:data\freeze.dat =Freeze

id: 9 type: 0 file:data\dennis.dat =Dennis

id: 10 type: 0 file:data\woody.dat =Woody

id: 11 type: 0 file:data\davis.dat =Davis



id: 100 type: 1 file:data\weapon0.dat #stick =木棒

id: 101 type: 1 file:data\weapon2.dat hoe =鐮刀

id: 120 type: 1 file:data\weapon4.dat #knife =小刀

id: 121 type: 4 file:data\weapon5.dat #baseball =棒球

id: 122 type: 6 file:data\weapon6.dat #milk =牛奶

id: 123 type: 6 file:data\weapon8.dat #beer =啤酒

id: 124 type: 1 file:data\weapon9.dat #< =回力標

id: 150 type: 2 file:data\weapon1.dat #stone =岩石

id: 151 type: 2 file:data\weapon3.dat #wooden_box =木箱

id: 217 type: 2 file:data\weapon10.dat #louis_armour =Louis的手腳盔甲

id: 218 type: 2 file:data\weapon11.dat #louis_armour =Louis的腰部盔甲

id: 300 type: 5 file:data\criminal.dat #criminal =人質



id: 200 type: 3 file:data\john_ball.dat =John的氣功波

id: 201 type: 1 file:data\henry_arrow1.dat =弓箭

id: 202 type: 1 file:data\rudolf_weapon.dat =飛鏢

id: 203 type: 3 file:data\deep_ball.dat =破空斬

id: 204 type: 3 file:data\henry_wind.dat =降龍掌

id: 205 type: 3 file:data\dennis_ball.dat =Dennis的氣功波

id: 206 type: 3 file:data\woody_ball.dat =Woody的氣功波

id: 207 type: 3 file:data\davis_ball.dat =Davis的氣功波

id: 208 type: 3 file:data\henry_arrow2.dat =穿空矢

id: 209 type: 3 file:data\freeze_ball.dat =冷凍波

id: 210 type: 3 file:data\firen_ball.dat =火焰彈

id: 211 type: 3 file:data\firen_flame.dat =豪火球

id: 212 type: 3 file:data\freeze_column.dat =冰霜拳

id: 213 type: 1 file:data\weapon7.dat #ice_sword =冰峰之劍

id: 214 type: 3 file:data\john_biscuit.dat =氣旋斬

id: 215 type: 3 file:data\dennis_chase.dat =追蹤波

id: 216 type: 3 file:data\jack_ball.dat =Jack的氣功波

id: 219 type: 3 file:data\jan_chaseh.dat =天使的祝福

id: 220 type: 3 file:data\jan_chase.dat =惡魔的審判

id: 221 type: 3 file:data\firzen_chasef.dat =殃殞天降中的火球

id: 222 type: 3 file:data\firzen_chasei.dat =殃殞天降中的冰球

id: 223 type: 3 file:data\firzen_ball.dat =炎冰砲

id: 224 type: 3 file:data\bat_ball.dat =激光眼

id: 225 type: 3 file:data\bat_chase.dat =吸血蝙蝠

id: 226 type: 3 file:data\justin_ball.dat =超能量摧毀炮

id: 228 type: 3 file:data\julian_ball.dat =連環重炮

id: 229 type: 3 file:data\julian_ball2.dat =極級破壞波



id: 998 type: 5 file:data\etc.dat =電腦的指令

id: 999 type: 5 file:data\broken_weapon.dat =毀壞的物件



id: 4 file: bg\sys\hkc\bg.dat =香港紅砌體育館

id: 2 file: bg\sys\lf\bg.dat =獅子山森林

id: 3 file: bg\sys\sp\bg.dat =赤柱監獄

id: 5 file: bg\sys\gw\bg.dat =萬里長城

id: 6 file: bg\sys\qi\bg.dat =皇后山(冰火山)

id: 7 file: bg\sys\ft\bg.dat =禁絕之塔

id: 1 file: bg\sys\cuhk\bg.dat =香港中文大學

id: 0 file: bg\sys\thv\bg.dat =大堪村

id: 10 file: bg\template\1\bg.dat =樣本背景1

id: 11 file: bg\template\2\bg.dat =樣本背景2

id: 12 file: bg\template\3\bg.dat =樣本背景3



◎id◎



id: ?

1.id帶有特性和像電腦的靈魂一樣，如id:1是電腦用deep的戰鬥模式，id:2是用

john的。

2.特性：id:6有1次盔甲防禦效果但不防冰火.Hp小於1/3時按DJA才可變身，id:37

有2次盔甲防禦效果但不防冰火，id:7.8當HP小於1/5時才可融合，id:8拳腳攻

擊打到別人的氣功波會反彈成冷凍波，id:51mp回復很快、在闖關中以敵軍

ratio來算等於兩個人，id:52有2次防禦、防冰火mp又回很快、闖關中以敵軍

ratio來算等於三個人，id:201.202的道具不受吹笛子、白色龍捲效果影響而且

射出去可以救人質，id:209的氣功波可將其他氣功波反彈成冷凍波，id:210.

220.221.222.223.225.224.226.228的氣功波不會被209的效果影響，id:223.

224的氣功波絕對只能直發無法上下移動。另外，分身分出來的人物id為5及52，

hp值為10。

3.id:0 ~ 29 在隨機選角色(闖關中寫成id:1000)會出現，或隨機選背景。30 ~39

、50 ~59是隱藏人物(背景)，要打lf2.net才會出現，100 ~ 199是會掉落的物

品。

4.(object到object_end之間)檔案(id)的總數不可超過100個，不然會造成遊戲

無法進入。



<特別發現>id:300的人物超強...





◎type◎



type:?

是指物件的種類

0:是沒有指定,人物是用這個種類

1:輕型武器

2.重型武器

3.是氣功波的類型,例如davis的氣功波

4.輕型武器(僅可投擲的)(例:棒球)

5.一個資料檔是包含著特殊的資料(例:criminal檔,即人質檔)

6.可以喝的物件





◎file◎



file:?

是指在哪個資料夾可以找到這個檔案

一般都是寫file: data\???.dat；???是指名稱,什麼名稱可直接打開data這個資

料夾看




## 關卡(stage)

先用stage.dat裡的其中一段為例:

<STAGE>id: 42 #stage 5-3

<PHASE>bound: 1500

id: 300 hp: 100 act: 40 x: 1300 y: 0 reserve: 5

id: 300 hp: 100 act: 50 x: 1300 y: 0 reserve: 5

id: 122 x: 300 #milk

id: 122 x: 300 #milk

id: 122 x: 300 #milk

id: 122 x: 300 #milk ratio: .7

id: 123 x: 300 #beer

id: 123 x: 300 #beer ratio: .7

id: 3000 hp: 50 times: 2 ratio: 1 <SOLDIER>

id: 1000 hp: 100 times: 2 <BOSS>

id: 34 hp: 100 times: 2 ratio: .5 join: 300

<PHASE_END>



id:人物/道具的id



以下是data.txt沒有的id:

3000是Bandit或Hunter(隨機)

1000是主角(id 0-29,隨機)

300 是人質(要出現甚麼人質,跟act有關,如act: 0就是monk,請用編輯器查看

criminal.dat)



hp:人物的hp

join:人物加入時的hp

times:人物重複出現的次數+1

ratio:我軍人數乘ratio=該人物出現數,如ratio是一以下,例: .5,我軍只有一個

人該人物便不會出現,要兩個以上才行

(2或以上乘.5=1或以上)



<BOSS>和<SOLDIER>:如果<BOSS>未死,<SOLDIER>便會不停出現(設定times的話

soldier就會失效)



bound:可移動範圍,數字愈大,移動範圍愈大,上限是2200(1-5,2-5,3-5,4-5,5-5

的上限是3000)



act:剛出現的指令,例: act:211 該人物便會一出現就跳

x:出現位置,例: x:300,該人物/道具便會在bound300的位置出現,可以是負數

y:出現高度,例: y:-500,該人物便會從天空降下來(此設定僅對人物有效)

reserve:人質復活次數(也可以用在別人身上)

#????:物件名稱(不打也可以)



<STAGE>闖關開始

id: xx闖關編號

#stage x-x哪一關

<PHASE>段落開始

<PHASE_END>段落結束

<STAGE_END>闖關結束

<END>全部結束



<特別發現>若從data.txt改變<BACKGROUND>的排序則闖關的場地會因之改變，因

執行檔執行的闖關背景是從第二行至第六行的bg。



※場地上最多物件350個，否則無法發氣功波(opoint)

※喝牛奶的時間99(喝造出來的牛奶時間是249)，喝酒的時間是154

※武器掉到場外即消失(闖關右側例外)

## 背景(background)

name: ??? 名稱

width: ? 地圖左右的寬度

zboundary: ? ? 地圖上下的範圍(第一個數字是上邊界的位置，第二個數字是下

邊界的位置)

shandow: bg\???\??\???.bmp 影子的圖片位置

shandowsize: ? ? 影子的尺寸(第一個數字是左右寬度，第二個數字是上下的寬

度)，它不會把圖片切掉

※人物站的位置是圖片的正中間。



layer: bg\sys\gw\s.bmp 圖片位置

transparency: ? width: ? x: ? y: ? cc: ? c1: ? c2: ? loop: ?

其他rect: ? height: ?

layer_end



layer是有照順序的，最後面敘述的(玩時)顯示在最前面

※layer_end不能加冒號(:)



transpparency: 0透明度(圖片黑色部分，0不透明，1透明)

width: 794是不會動(圖片在整場移動距離=?-794)

x: x座標

y: y座標，最高點110

loop: 多少距離放一個圖片

cc: 多少時間循環一次

c1: 循環內出現的時間

c2: 循環內結束的時間

示意圖：

←╮

╰→→→→→→→→→→→→╯

c1→出現→c2 cc



rect: 色彩填滿

width: 寬度(從x座標算起)

height: 高度(從y座標算起)


<以上正文>

和這個：
<抓人方法>
   itr:
      kind: 3 x: 21 y: 34 w: 40 h: 28 vrest: 7
      catchingact: 120 120 caughtact: 130 130
   itr_end:
--

## 文獻資料來源
- https://forum.gamer.com.tw/Co.php?bsn=7648&sn=20883