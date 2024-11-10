aachip_BIN_HEX_TO_MEM 說明書

本程式是專門用在設計MCU IP 時需要將MACHINE CODE 轉成mem檔案
方便在Simulation 軟體上做你的MCU Debug.

1.首先先確認你的mcu 程式轉出來的bin 或 hex 是成功的.
2.打開aachip_BIN_HEX_TO_MEM.
3.選擇你要轉換檔案的格式是bin 或是hex
4.點擊你要轉換的程式.

5.選擇你的mcu bit模式,如果是8051 選擇8bit模式.
6.如果是16bit mcu 選擇16bit模式.
7.如果是riscv or arm或者標示32bit, 選擇32bit模式.
8.特殊mcu如果有12bit,14bit則沒有支援.
9.16bit和32bit都可以選擇你的mcu是高位置在前還是後.
10.重點是Simulation 預設記憶體的大小,跟你的MCU Memory有關.
  需要符合你的MCU Memory大小.
11.在你的verilog或是vhdl設定memory address時,
如果是8bit memory address 跟cpu address需要連線是an~a0==an~a0
如果是16bit memory address 跟cpu address需要連線是an~a0==an+1~a1
如果是32bit memory address 跟cpu address需要連線是an~a0==an+2~a2
這是測試出來可以run的方法,如果有其他的解決方法,歡迎討論改進.

10.按下開始轉換後,如果成功則會顯示寫入你轉出的檔案.mem
11.你可以用編輯程式打開轉換好的.mem,
這個例子式32bit所以會有每8個hex一個空白
12.一行有8個 8個hex;wordsperline如果設為2則一行有2個 32bit
13.接下來你可以打開你的fpga軟體,我使用的是altera quartusii,打開RTL Simulation.
14.這時候就會出現ModelSim.前提是你已經跑成功altera quartusii爾且沒有出現錯誤.
15.ModelSim出現後,你再選擇你要Simulation的主程式,這裡是test.v 
16.Simulation成功後會出現Sim 及 Memory List .
17.Sim 裡面是你要看的訊號選擇出來.
18.Memory List就是將我們的.mem放到你要的地方.
19.這個例子我們是放在TEST/TOP/R1/ram裡面,點擊後,右邊出現記憶體的區域,
20.按下右鍵選擇Import Data patterns,在file name裡面選到你剛剛轉換出來的mem的位置,選到該程式.
21.按下ok後;mem的檔案就import近來了.
22.選擇你要simulation的長度後,我選擇1us,然後按下run,等到完成後就會停止你就可以看所有mcu執行的過程.
23.注意1.如果一開始ModelSim 只有run一下就停止,你就重新按一下reset,也就是icon往上的那個.
24.注意2.每次你reset你的Simulation後需要重新import 你的mem,但是不需要重新點擊位置,
可以參考https://www.youtube.com/@AACHIP-ku3kt 如何使用

