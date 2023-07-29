# MAC 日本語キーボードでまともにリモートデスクトップを使いたい方へ

## 必要なパッケージのインストール

brew install pkcs11-helper
brew install cjson
brew install sdl2_ttf
(brew install openssl@3 も必要かも？インストールされていなければ)

## ビルド(バイナリをダウンロードする場合は不要)

* brew upgrade (brew install cmake で cmake 3.27 より古いバージョンが入ってしまう場合)
* brew install cmake
* xcode をインストール
* sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer が必要かも？(*1)
* make -S . -B build -DWITH_CLIENT_SDL=ON -DWITH_CLIENT_MAC=OFF

(*1) 「xcode-select: error: tool 'ibtool' requires xcode, but active developer directory '/library/developer/commandlinetools' is a command line tools instance」のようなエラーが出る場合。

これで build/client/SDL/sdl-freerdp にバイナリができる。

## インストール

sdl-freerdp を /usr/local/bin など、適当な場所にコピー。

## 起動

ターミナルを開き、以下のコマンドを実行

sdl-freerdp /v:接続先 /u:ユーザ名 /p:パスワード /kbd:layout:Japanese,lang:0x0411 /dynamic-resolution /sound /microphone /video

