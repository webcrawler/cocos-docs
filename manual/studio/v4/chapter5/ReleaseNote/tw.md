# **版本更新說明：** #

**&emsp;&emsp;Cocos 2.3.1版本更新內容：**


 &emsp;&emsp;【新增】自訂Cocos Framework & Simulator功能。（**"Cocos Framework 3.7支持，文檔：http://www.cocos.com/doc/**）

 &emsp;&emsp;【新增】專案設置增加全部發佈選項。

 &emsp;&emsp;【新增】Cocos增加API文檔，支援複製粘貼。

 &emsp;&emsp;【新增】偏好設置增加簡化控制項（按鈕，核取方塊，滑動條）初始資源功能。（**"文檔：http://www.cocos.com/doc/**）

 &emsp;&emsp;【新增】藝術字體控制項支援首字元，字元寬，字元高設置。
 
 &emsp;&emsp;【新增】ttc格式字體支援描邊設置。

 &emsp;&emsp;【新增】FAQ新增修復打包失敗文檔。（**文檔：http://www.cocos.com/doc/**）

 &emsp;&emsp;【優化】字體描邊演算法，描邊效果更合理。


 &emsp;&emsp;【優化】去掉解析"xxx missed"顯示。(**Cocos Framework 3.7支持**)。


 &emsp;&emsp;【優化】Windows模擬器功能表顯示改為標題列右鍵彈出功能表，擴大調試區域。


 &emsp;&emsp;【優化】控制項面板和屬性面板UI，增強操作性。


 &emsp;&emsp;【優化】JS專案資源不需要添加到src/resource.js，流覽器運行也可以正常顯示。（**Cocos Framework 3.7支持**）



 &emsp;&emsp;【優化】陰影偏移量支援兩位元小數，提高陰影效果精確度。


 &emsp;&emsp;【優化】Cocos文檔頁面支援複製粘貼。


 &emsp;&emsp;【優化】Cocos回饋頁面增加常見問題解答。


 &emsp;&emsp;【修復】打開專案，描邊寬度1變為0的問題。


 &emsp;&emsp;【修復】C++專案編輯資源後發佈到VS運行，資源刷新不及時的問題。（**Cocos Framework 3.7支持**）


 &emsp;&emsp;【修復】在結構樹重命名時按下Shift+B/T/Q/W會結束編輯狀態的問題。

**&emsp;&emsp;Cocos 2.3.0版本更新內容：**

 &emsp;&emsp;【新增】3D場景內多個物體選中後，參考坐標軸和原點的快速切換功能。

 &emsp;&emsp;【新增】尺規與輔助線在場景，節點和圖層。

 &emsp;&emsp;【優化】以JSON檔案格式發佈時，將場景資源清單存儲到對應的.json文件中。

 &emsp;&emsp;【優化】3D場景網格輔助線。

 &emsp;&emsp;【優化】功能表增加隱藏/顯示錨點，Windows快速鍵為 ctrl + shift + A，
Mac平臺的快速鍵為Command+Shift+A。

 &emsp;&emsp;【優化】Cocos説明文檔，啟動介面內置文檔模組，方便快速查看。

 &emsp;&emsp;【修復】描邊寬度為0，遊戲載入效果仍然顯示描邊效果的問題。

 &emsp;&emsp;【修復】替換fnt字體，刷新資源區，渲染區不更新的問題。


**&emsp;&emsp;Cocos 2.2.9版本更新內容：**

 &emsp;&emsp;【修復】plist合圖匯出png時，合圖中含有透明屬性的圖片丟失。

**&emsp;&emsp;Cocos 2.2.8版本更新內容：**

 &emsp;&emsp;【新增】點擊3D世界坐標軸可快速調節視圖。

 &emsp;&emsp;【新增】點擊四個方向鍵可快捷移動3D場景。

 &emsp;&emsp;【新增】3D場景默認添加一個攝像機。

 &emsp;&emsp;【新增】支援3D對象快速等比例縮放。

 &emsp;&emsp;【新增】支援2D畫布移動的手型按鈕和快速鍵：點擊手型按鈕（Q）後開啟移動畫布功能，點擊箭頭按鈕（W）恢復到常態。

 &emsp;&emsp;【優化】匯出Lua以外掛程式形式在Cocos Store提供。

 &emsp;&emsp;【優化】優化Launcher介面，支援打開專案、打開專案所在資料夾。

 &emsp;&emsp;【優化】Launcher教程頁添加cocos入門英文教程。

 &emsp;&emsp;【優化】資源區刪除功能，支援從專案移除索引或者刪除到回收站。

 &emsp;&emsp;【修復】編輯器匯出資料檔案中，PercentWidthEnabled以及PercentHeightEnabled不更新的問題。

**&emsp;&emsp;Cocos 2.2.6版本更新內容：**
    
 &emsp;&emsp;【修正】打開含有較多合圖檔的專案，合圖檔中的圖片丟失。

**&emsp;&emsp;Cocos 2.2.5版本更新內容：**
                                    
 &emsp;&emsp;【新增】一鍵部署並運行app在iOS、Android、win32、Mac以及流覽器平臺上。

 &emsp;&emsp;【新增】JS項目可以打包成Html5 App。

 &emsp;&emsp;【新增】支援3D控制項擴展。

 &emsp;&emsp;【新增】資源面板csd檔支援拷貝操作，快速鍵為Ctrl/Command+D。

 &emsp;&emsp;【新增】按兩下嵌套的csd檔， 直接進入編輯狀態。

 &emsp;&emsp;【新增】按鈕和文本控制項增加描邊、陰影屬性設置。(**Cocos 2d-x 3.6支持解析**)

 &emsp;&emsp;【新增】動畫緩動設置。（Cocos 2d-x 3.6支持解析）。

 &emsp;&emsp;【新增】精靈控制項，粒子控制項blending功能。（**Cocos 2d-x 3.6支持解析**）

 &emsp;&emsp;【新增】取色器面板支援顏色歷史記錄。

 &emsp;&emsp;【新增】多選結構樹節點，可批量操作顯示與鎖定。

 &emsp;&emsp;【優化】完整專案與資源專案整合為cocos專案，簡化創建專案流程。

 &emsp;&emsp;【優化】資源專案可以升級為完整專案。

 &emsp;&emsp;【優化】支援快速鍵（Shift + Q/W/T/B）控制調整物件的渲染層級。

 &emsp;&emsp;【優化】創建序列幀動畫，增加“是否追加第一幀為最後一幀”選項，可方便的創建迴圈的序列幀動畫。
 
 &emsp;&emsp;【優化】去掉節點不可以重名的判斷。

 &emsp;&emsp;【優化】九宮格參數可以更直觀的通過拖動的方式進行設置。

 &emsp;&emsp;【優化】給控制項設置資源，控制項的尺寸將預設設置為資源的尺寸。

 &emsp;&emsp;【優化】3D網格輔助線顯示。

 &emsp;&emsp;【優化】圖層（Layer）檔嵌套可以參與佈局，做UI介面更加實用。

 &emsp;&emsp;【優化】整合發佈與打包介面。

 &emsp;&emsp;【修復】導入1.6 UI專案只改變結構樹顯示，不改變控制項可見性，導致模擬器裡面仍然顯示的問題。

 &emsp;&emsp;【修復】ScrollView Area大小受content size限制的問題。                        
                                                                        
**&emsp;&emsp;Cocos 2.2.1版本更新內容：**
    
 &emsp;&emsp;【修復】編輯器匯出的合圖檔會多增加.plist副檔名的問題。

**&emsp;&emsp;Cocos 2.2版本更新內容：**
    
 &emsp;&emsp;【重磅推出】3D場景編輯——新增模型支援、粒子特效、攝像機控制項，遊戲製作功能更強大（**Cocos 2d-x 3.5支援解析**）。

 &emsp;&emsp;【萬眾期待】支援基於Lua腳本的自訂控制項，擴展隨心所欲 。

 &emsp;&emsp;【新增】Cocos商店華麗變身，下載、安裝、卸載一鍵搞定，資訊和評論與你分享。

 &emsp;&emsp;【新增】支援修改動畫播放速度，預覽演示更方便 （**cocos2d-x 3.5支援解析**）。

 &emsp;&emsp;【新增】多解析度設置，常用解析度自由設定 。
 
 &emsp;&emsp;【新增】控制項高級屬性可設置自訂資料 （**Cocos 2d-x 3.5支援解析**）。

 &emsp;&emsp;【優化】編輯器匯出的資料，支援Cocos 2d-x 3.4 Final載入。
 
 &emsp;&emsp;【優化】新建專案與示例工程合併，創建專案更便捷 。

 &emsp;&emsp;【優化】對新創建的專案進行Name屬性校驗， 保證變數名有效。

 &emsp;&emsp;【優化】支援在屬性區修改圖層尺寸。

 &emsp;&emsp;【優化】固定與拉伸佈局屬性， 支援直接輸入數值進行設置。

 &emsp;&emsp;【優化】控制項可設置禁用的圖片。

 &emsp;&emsp;【優化】Button控制項支援清空預設資源， 減小資源大小。

 &emsp;&emsp;【優化】csd文件外部編輯後的同步問題。
 
 &emsp;&emsp;【優化】專案打開速度大幅提升。

 &emsp;&emsp;【修正】Mac OS X 10.10.2自動升級閃退的bug。


注意：Cocos2d-x 3.4（含）以上的版本支持cocos 2.2（含）以上的版本发布的数据。
