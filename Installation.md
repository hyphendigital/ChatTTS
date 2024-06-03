# Installation

## Install and Run on MacBook Pro M-Chips
### Install
``` Shell
$ git clone https://github.com/2noise/ChatTTS.git & cd ChatTTS
➜  ChatTTS git:(main) ✗ pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple // 按需替换国内源
➜  ChatTTS git:(main) ✗ vi ChatTTS/core.py // 关闭do_text_normalization开关，置为False，因为pip安装WeTextProcessing失败，导致报错，见issue：https://github.com/2noise/ChatTTS/issues/160
```
### Run
国内无法链接HuggingFace，见中文版README，替换成本地的模型，下载安装参考：https://www.modelscope.cn/models/pzc163/chatTTS/summary
``` Shell
➜  ChatTTS git:(main) ✗ ~/venv/bin/python3
Python 3.12.3 (main, Apr  9 2024, 08:09:14) [Clang 15.0.0 (clang-1500.3.9.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from modelscope import snapshot_download
2024-06-03 15:18:38,117 - modelscope - INFO - PyTorch version 2.2.2 Found.
2024-06-03 15:18:38,117 - modelscope - INFO - Loading ast index from /Users/xxx/.cache/modelscope/ast_indexer
2024-06-03 15:18:38,117 - modelscope - INFO - No valid ast index found from /Users/xxx/.cache/modelscope/ast_indexer, generating ast index from prebuilt!
2024-06-03 15:18:38,262 - modelscope - INFO - Loading done! Current index file version is 1.14.0, with md5 0113db1cdf9804cfb52afcff67baeeca and a total number of 976 components indexed
>>> model_dir = snapshot_download('pzc163/chatTTS')
Downloading: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 47.0/47.0 [00:00<00:00, 105kB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 98.9M/98.9M [00:11<00:00, 9.02MB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 117/117 [00:00<00:00, 1.41MB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 26.5M/26.5M [00:03<00:00, 8.78MB/s]
Downloading: 100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 143/143 [00:00<00:00, 569kB/s]
Downloading:   0%|                                                                                                                                                                                                                                   | 0.00/859M [00:00<?, ?B/s]

Downloading: 100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▉| 859M/859M [01:50<00:00, 8.14MB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 346/346 [00:00<00:00, 1.41MB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 309/309 [00:00<00:00, 1.29MB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.36k/1.36k [00:00<00:00, 5.91MB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 4.16k/4.16k [00:00<00:00, 6.89MB/s]
Downloading: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 329k/329k [00:00<00:00, 4.24MB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 51.8M/51.8M [00:11<00:00, 4.87MB/s]
Downloading: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 460/460 [00:00<00:00, 2.06MB/s]
>>>
>>>
>>> print(model_dir)
/Users/xxx/.cache/modelscope/hub/pzc163/chatTTS
```
Then:
``` Shell
➜  ChatTTS git:(main) ✗ ~/venv/bin/python3 webui.py --local_path="/Users/xxx/.cache/modelscope/hub/pzc163/chatTTS"
```