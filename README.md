# robosys2020
ロボットシステム学の課題用に作成
## 概要
デバイスドライバを作成し、7セグメントLEDを光らせて1~6の数字を表示させるプログラム.

## 動作環境/使用したもの
- Raspberry Pi Raspberry Pi 3 Model B+
- Ubuntu20.04 server
- ブレッドボード
- 7セグメントLED(アノードコモン)
- ジャンパー線
- 抵抗器 220Ω

## 回路
以下の図のように回路を作成
LEDをRaspberry PiのGPIO｛16, 17, 18, 19, 20, 23, 27}に接続
![kairo](https://user-images.githubusercontent.com/55970079/101341242-21fe6e00-38c4-11eb-982f-6afa25a7af5c.jpg)

下の図に各LEDが対応しているGPIOを記載
![led](https://user-images.githubusercontent.com/55970079/101341014-d21fa700-38c3-11eb-91e5-9836f4f9fdfb.png)

## 実行手順
以下のコマンドを順番に行う

まずこのリポジトリをクローンしてくる

`git clone https://github.com/Souya25/robosys2020.git`

ディレクトリを移動

`cd robosys2020`


makeするコマンド

`make`

カーネルモジュールのロード

`sudo insmod myled.ko`

読みとりと書き込みの権限を付与

`sudo chmod 666 /dev/myled0`

下のコマンドで、1~6の数字からランダムに選ばれLEDが光る

`echo $((RANDOM%6+1)) > /dev/myled0`

LEDを消灯させるとき

`echo - > /dev/myled0`

後処理をする

`sudo rmmod myled`

`make clean`

## 実際の映像
[YouTube](https://www.youtube.com/watch?v=YTrZ0EsbJqY&feature=youtu.be)

