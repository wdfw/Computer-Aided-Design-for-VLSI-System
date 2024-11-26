1. 學號：B10902227
2. 姓名：吳宗喬
3. 程式語言：C++
4. 編譯平台：Linux GNU g++
5. 檔案壓縮指令: tar zcvf b10902227-p2.tgz b10902227-p2
6. 檔案解壓縮指令 : tar zxvf b10902227-p2.tgz
7. 檔案說明：
	b10902227-p2/SlicingTree.hpp  	: Slicing tree data structure defination.
	b10902227-p2/SlicingTree.cpp 	: Slicing tree data structure.
	b10902227-p2/Block.hpp 	: Block data structure defination.
	b10902227-p2/Block.cpp 	: Block data structure.
	b10902227-p2/main.cpp 	: Implement floorplan with SA and slicing tree.
  	b10902227-p2/Makefile	: Makefile
	b10902227-p2/readme.txt	: 本檔案
	b10902227-p2/report.docx: 介紹所使用演算法與資料結構
8. 執行流程
	1. 進入資料夾 b10902227-p2
	2. 輸入 make 並產生執行檔 floorplanner
	3. 執行 floorplanner (執行格式 : ./floorplanner [input file name] [output file name])
	4. 生成 .out 檔
9. 顯示與輸出
	在開始執行時輸出框會顯示Original Area，Original Aspect Ratio，Original Cost，
	代表初始隨機的放置面積，高寬比與成本
	執行時會有進度條，執行完成會顯示執行時間，
	最後會輸出*.out檔，並在顯示框顯示Optimal Area，Optimal Aspect Ratio，Optimal Cost，
	代表SA找到最佳結果的放置面積，高寬比與成本。　　
