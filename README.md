# COI-NEXT-device
Googleドライブに音声データをアップロードするデバイスシステム

# 環境
- Raspberry Pi 4 or 3B+
- Rasbian
- python3.9以上

## 初期設定
1. clone this repository & `cd COI-NEXT-device`
2. `startUp.py`を実行
3. 必要ライブラリをインストール
```bash:Terminal
sudo apt update 
sudo apt upgrade
sudo pip install --break-system-packages --upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib oauth2client
sudo apt install python3-pyaudio
```
4. Google Cloud Platformにログインし認証用のJSONファイルをダウンロードしてくる。名前を`client_secret.json`に変更する。
5. Jsonファイルから`token.json`を生成する
    - 生成にはブラウザを使用するためGUIが使えない場合は別で生成しておくことをお勧めする
    - `token.json`は`uploadToGoogleDrive.py`と同じ階層に置く
6. `test/showRecodingDevice.py`を動かし使用するオーディオインターフェースのデバイス番号を調べる
7. 調べたデバイス番号で`recoding.py`を設定する。（必要なら録音時間なども編集）

## 実行方法
```bash:Terminal
python recoding.py &
python uploadToGoogleDrive.py &
```
sshなどで接続している場合はnohupなどを使用することをオススメする

