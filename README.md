# COI-NEXT-device
Googleドライブに音声データをアップロードするデバイスシステム

# 環境
- Raspberry Pi 4 or 3B+
- Rasbian
- python3.9以上

## 初期設定
1. `startUp.py`を実行
1. 必要ライブラリをインストール
```bash:Terminal
sudo apt update 
sudo apt upgrade
sudo pip install --upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib oauth2client
sudo pip3 install pyaudio
sudo apt install libportaudio0 libportaudio2 libportaudiocpp0 portaudio19-dev
```

## 使用方法
2. Google Cloud Platformにログインし認証用のJSONファイルをダウンロードしてくる。
2. Jsonファイルから`token.json`を生成する
    - 生成にはブラウザを使用するためGUIが使えない場合は別で生成しておくことをお勧めする
    - `token.json`は`uploadToGoogleDrive.py`と同じ階層に置く
2. `test/showRecodingDevice.py`を動かし使用するオーディオインターフェースのデバイス番号を調べる
2. 調べたデバイス番号で`recoding.py`を設定する。（必要なら録音時間なども編集）
2. `recoding.py`と`uploadToGoogleDrive.py`を実行する

## 実行方法
```bash:Terminal
python recoding.py &
python uploadToGoogleDrive.py &
```
sshなどで接続している場合はnohupなどを使用することをオススメする

