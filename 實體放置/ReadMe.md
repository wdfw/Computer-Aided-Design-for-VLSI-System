## 專案說明
在本次專案中，我們要透過Slincing Tree這個資料結構保存元件的位置，並透過Simulated Annealing (SA)這個啟發式的演算法
不斷通過對Slincing Tree的各種交換操作，改變元件位置，嘗試在限制電路長寬比的情況下最小化電路的總面積。
## 檔案說明  
main.cpp: 輸入與輸出的主檔案  
SlicingTree.hpp: 定義Slicing tree的結構與可行的操作  
SlicingTree.cpp: 實現Slicing tree的資料結構與其操作  
Block.hpp: 定義元件資料(包含長寬，位置等資訊)  
Block.cpp: 實現顯示元件資訊等操作  
report.pdf: 程式的執行狀況與我在實踐上加強的部分  
sample.txt: 測試用的元件資料
## 使用方法
	1. 進入此資料夾
	2. 輸入 make 並產生執行檔 floorplanner
	3. 執行 ./floorplanner [input file name] [output file name]
 		input file name: 輸入的元件資料
   		output file name: 輸出的.out檔
	4. 生成 .out 檔
 
## 執行狀況
在開始執行時輸出框會顯示Original Area，Original Aspect Ratio，Original Cost，代表初始隨機的放置面積，高寬比與成本(面積)，
執行時會有進度條，執行完成會顯示執行時間，最後會輸出*.out檔，  
並在顯示框顯示Optimal Area，Optimal Aspect Ratio，Optimal Cost，代表SA找到最佳結果的放置面積，高寬比與成本。
