# FPGA-based System Design - Lab02 HW

## 成員名單
E24041022、E24041894、E24046674

## Program 1.
使用兩顆 RGB LED 實作十字路口的紅綠燈。

我們的程式碼是先利用之前提供過的除頻器來降頻，因為原本的clock速度太快，肉眼無法觀察出LED的變化。
然後當除頻後的clock'(大約頻率1秒)一來，counter就會+1，依此來決定紅綠燈，當其中一個為綠燈時，另一個為紅燈。
由於綠燈為15秒，當counter數到15的時候，綠燈會變成黃燈，紅燈會維持著，當第16秒時，黃燈會變紅燈，而紅燈會變綠燈。

#### BUTTON
● 當按下button1時，會reset counter的值，從新開始計數。

● 當按下button2時，我們的寫法是直接讓counter變16，所以會導致紅綠燈交換，也是作業第2點的需求。

● 當按下button3時，會讓綠燈縮減成7秒，所以只會有3個LED來顯示時間。


## Program 2.
使用按鈕調整 RGB LED 的 RGB值。

我們的程式碼是先判斷各個switch之後，再去決定按下button會發生的事，而我們的clock也是利用之前的除頻器來降頻。

● 當switch為 "00" 的時候，我們設計的程式碼是 "按著" button2，才會使LED亮著根據R、G、B的PWM值決定亮的時間長短。

● 當switch為 "01" 的時候，可以調整R的PWM值，我們的程式碼是把PWM MAX設為300(每個週期大概15秒)，也就是依據LED 4個bits(0~15)，每按下button3(增加一次)會多20的PWM值(1秒)，相對的，按下button4(減少一次)會少20的PWM值(1秒)。

● 當switch為 "10" 的時候，可以調整G的PWM值，我們的程式碼是把PWM MAX設為300，也就是依據LED 4個bits(0~15)，每按下button3(增加一次)會多20的PWM值，相對的，
按下button4(減少一次)會少20的PWM值。

● 當switch為 "11" 的時候，可以調整B的PWM值，我們的程式碼是把PWM MAX設為300，也就是依據LED 4個bits(0~15)，每按下button3(增加一次)會多20的PWM值，相對的，
按下button4(減少一次)會少20的PWM值。

問題討論: 由於我們當初看作業需求，以為要按著button2才會持續發光，所以我們在決定RGB要亮的時候，無法把PWM的clock歸零，導致RGB在switch為"00"的時候
按下button2，可能是counter跑到一半，導致不會亮的情形發生，但只要等到下一個週期，就可以看出各RGB依據PWM值決定亮的時間。


### ★由於這次作業結果極難以用圖片表示，所以我們把demo影片拍了下來，藉此說明其運作。
Program1 :  https://drive.google.com/open?id=1lD-5-4gnBIhAD28i-QegqAJrKgxfc-1R

Program2 :  https://drive.google.com/file/d/1hCDX51ExqZe-G85jkRmhQ79zzOJ1IcnZ/view?usp=sharing


### 希望助教不要介意QQ


