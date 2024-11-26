## 專案說明
在本次專案中，我們要實現全局繞線的演算法，我透過A*-search演算法在電路中根據不同元件的特性(例如:有的元件可以穿過但有的步行)，繞出一條成本較低的路徑，目標是在完成
所有繞線的情況下最小化總體的成本(包含繞線長度，密度，元件的硬限制等等)。
## 檔案說明  
main.cpp: 執行整個流程的主程式  
Parser.hpp: 輸入檔案解析器定義  
Parser.cpp: 輸入檔案解析器的實現，處理DEF/CFG/Connection matrix等格式的檔案  
CircuitStructure.hpp: 舊的資料結構定義  
CircuitStructure.cpp: 舊的資料結構實現  
NewCircuitStructure.hpp: 新的資料結構與演算法定義  
NewCircuitStructure.cpp: 新的資料結構與演算法實現  
Utils.hpp: 其他的小工具  
Utils.cpp: 小工具的實現  
DrawBmp.hpp: 畫.bmp的程式  
test_case: 測試資料夾(只有小型資料，因為大型比賽資料目前程式跑不動)  
routingResult.bmp: 測試產生的佈線圖  
net.rpt: 測試產生的佈線檔
## 使用方法
        1. 進入資料夾
        2. 輸入 make 並產生執行檔 CGR
        3. 執行 CGR 
          輸入格式 : ./CGR [XX] [caseOO.def] [caseOO.cfg.json] [caseOO.connection_matrix.json] [outputfile] [-f] [-s] 
           Ι.    XX代表邊可容納的track數(tracks/um)
                 (輸入的tracks/um要大於net檔案的最大值才可以繞線，因為gcell部分尚未完成，若太小會跳出錯誤並顯示net檔中的最大值)
           ΙΙ.   caseOO.def為DEF格式的檔案
           III.  caseOO.cfg.json為block狀態
           IV.   caseOO.connection_matrix.json為net的定義
           V.    outputfile為輸出檔名稱，可以不用
           VI.   -f會使輸出只顯示繞線失敗的資訊
           VII.  -s會關閉所有繞線成功/失敗的資訊
        4. 輸出佈線檔案(未指定outputfile下為net.rpt) 與 佈線圖(routingResult.bmp)

## 測試結果
以下是輸入 ./CGR 1000 test_case/case33/case33_def test_case/case33/case33_cfg.json test_case/case33/case33.json 產生的佈線圖
![image](https://github.com/user-attachments/assets/070b30d9-1c69-405e-b14b-e0c513427f0d)
## 執行狀況
執行程式後會根據輸入檔案進行繞線，執行過程會顯示繞成功與失敗的net (可用-f與-s關閉)  
成功會顯示Complete ID: [# of nets] of [net ID]，[# of nets]代表此net ID的第#條線，[net ID]代表net ID  
失敗會顯示Non-throughable ID: [# of nets] of [net ID]，同上  
每次成功/失敗都會顯示總共完成的繞線數量(Total Completed: # Nets)  
而最後會顯示成功繞線的比例(Routable Rate: #%)  
最後會輸出 佈線檔案(預設為net.rpt) 與 佈線點陣圖(routingResult.bmp)   
佈線點陣圖包含元件與佈線，白色為晶片，紅色為feedthrough_block，黑色為non-feedthrough_block，深藍色為佈線，黃色為佈線目標，淺藍為佈線起始點  






        
