# OpenVINO_human-pose-estimation

human_pose_estimation_demo 範例程式來源為Intel OpenVINO 2019 R2版，預設安裝後會於下面路徑
C:\Program Files (x86)\IntelSWTools\openvino_2019.2.242\deployment_tools\open_model_zoo\demos\human_pose_estimation_demo

預設安裝後會在下面路徑找到Visual Studio 的專案檔
C:\Users\使用者名稱\Documents\Intel\OpenVINO\inference_engine_demos_build\Demos.sln

使用Visual Studio 2017編譯後，執行檔會產生於下面路徑：
C:\Users\jack_\Documents\Intel\OpenVINO\inference_engine_demos_build\intel64\Release\human_pose_estimation_demo.exe

執行前必須先設定環境變數，執行指定批次檔。
C:\Program Files (x86)\IntelSWTools\openvino_2019.2.242\bin\setupvars.bat

另外須要下載預訓練模型已優化中介檔（bin, xml)

/* 切換至下載工具路徑 */
cd C:\Program Files (x86)\IntelSWTools\openvino_2019.2.242\deployment_tools\tools\model_downloader
/*下載預訓練模型到指定路徑 */
python3 downloader.py --name human-pose-estimation-0001 --output_dir 使用者指定路徑
/* 指定路徑下的優化模型IR中介檔存放路徑 */
\使用者指定路徑\Transportation\human_pose_estimation\mobilenet-v1\dldt\
包含\INT8, \FP16, \FP32三種格式的IR檔，human-pose-estimation-0001.bin 及 human-pose-estimation-0001.xml

執行指令：
human_pose_estimation_demo -i 輸入影片檔名(*.mp4, *.avi) -m \使用者指定路徑\Transportation\human_pose_estimation\mobilenet-v1\dldt\FP16\human-pose-estimation-0001.xml -d CPU

其中FP16可替換成 INT8 或 FP32，以不同數值精度計算。
而最後一個參數 -d 則是用來指定不同執行裝置包括 CPU, GPU, MYRIAD，前二者三種精度皆可執行，但MYRIAD (就是VPU或稱神經運算棒NCS）只能執行FP16格式。

若要直接以網路攝影機當作輸入，則將指令改為 -i cam 即可，預設是電腦上第一組攝影機(cam0)，執行後按ESC鍵可結束。


OpenVINO土炮體感控制系統 （完整說明文章待更新...）
