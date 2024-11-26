電子設計自動化軟體開發與實作 期末專案	
組別: 第六組 
組員: B10902227吳宗喬、B10902116林怡薰

1. 程式語言: C++
2. 編譯平台: Linux GNU g++
3. 檔案壓縮指令: tar zcvf group_6.tgz group_6
4. 檔案解壓縮指令: tar zxvf group_6.tgz
5. 檔案說明：
        group_6/Parser.cpp: 輸入檔案解析器定義
        group_6/Parser.hpp: 輸入檔案解析器的實現，處理題目D的DEF/CFG/Connection matrix檔案

        group_6/CircuitStructure.hpp: 舊的資料結構定義
        group_6/CircuitStructure.cpp: 舊的資料結構實現

        group_6/NewCircuitStructure.hpp: 新的資料結構與演算法定義
        group_6/NewCircuitStructure.cpp: 新的資料結構與演算法實現

        group_6/Utils.hpp: 其他的小工具
        group_6/Utils.cpp: 小工具的實現
        
        group_6/DrawBmp.hpp: 畫.bmp的程式

        group_6/main.cpp: 主流程執行程式

        group_6/Makefile: Makefile
        group_6/readme.txt: 本檔案
        group_6/test_case: 測試資料(只有小型資料，因為比賽資料目前程式跑不動)
        group_6/slides.ppt 期末報告投影片
        group_6/image.png 繳交證明
        
6. 執行流程
        1. 進入資料夾 group_6
        2. 輸入 make 並產生執行檔 CGR
        3. 執行 CGR 
        　 輸入格式 : ./CGR XX caseOO.def caseOO.cfg.json caseOO.connection_matrix.json [outputfile] [-f] [-s] 
           Ι.    XX代表邊可容納的track數(tracks/um)
                 (輸入的tracks/um要大於net檔案的最大值才可以繞線，因為gcell部分尚未完成，若太小會跳出錯誤並顯示net檔中的最大值)
           ΙΙ.   caseOO.def為DEF格式的檔案
           III.  caseOO.cfg.json為block狀態
           IV.   caseOO.connection_matrix.json為net的定義
           V.    outputfile為輸出檔名稱，可以不用
           VI.   -f會使輸出只顯示繞線失敗的資訊
           VII.  -s會關閉所有繞線成功/失敗的資訊
        4. 輸出佈線檔案(未指定outputfile下為net.rpt) 與 佈線圖(routingResult.bmp)
        
        make產生執行檔後輸入以下指令可以完成以上流程
        ./CGR 1000 test_case/case33/case33_def test_case/case33/case33_cfg.json test_case/case33/case33.json 
            
7. 執行說明
        執行程式後會根據輸入檔案進行繞線，執行過程會顯示繞成功與失敗的net (可用-f與-s關閉)
        成功會顯示Complete ID: [# of nets] of [net ID]，[# of nets]代表此net ID的第#條線，[net ID]代表net ID
        失敗會顯示Non-throughable ID: [# of nets] of [net ID]，同上
        每次成功/失敗都會顯示總共完成的繞線數量(Total Completed: # Nets)
        而最後會顯示成功繞線的比例(Routable Rate: #%)
        最後會輸出 佈線檔案(預設為net.rpt) 與 佈線點陣圖(routingResult.bmp)
        佈線檔案遵守題目D的輸出
        佈線點陣圖包含元件與佈線，白色為晶片，紅色為feedthrough_block，黑色為non-feedthrough_block
                              ，深藍色為佈線，黃色為佈線目標，淺藍為佈線起始點

8. 程式新增加的部分(與簡報比較)
        1. 繞線檔案輸出
        2. A*-search的cost原本只有 起始距離 與 估測終點距離，現在新增繞線成本(公式與簡報相同)
        3. 更完整的顯示繞線資訊

9. 程式的實現內容
        截至目前，本專案實現了D問題global router的完整流程，從輸入的文本進行剖析並建立
        資料結構，再利用資料結構建立grid上的物件來實現A*-search演算法，接著以A*-search為
        檔案中的每條線進行繞線，最後將所有繞線的點轉成線段輸出。雖然已經實現了完整的流程，
        但有些細節，如重疊原件，gcell處理與一些block的屬性(must_through)與演算法的優化還
        尚未實作出來，因此對比賽的測資目前還無法完成，但在輸入沒錯且資料量不龐大下仍可以完
        成繞線，雖然很可惜無法完成比賽要求，但本次專案也令我對EDA領域的專案設計有些許體驗，
        感謝教授與助教在課堂的設計與協助讓我了解EDA的有趣之處。






        