# ROS2 Windows template for VSCode

Windows の VSCode で ROS2 humble を扱うためのひな形。
このリポジトリでは例として、[ros2/examples](https://github.com/ros2/examples/tree/humble) をビルド・実行できる。


## ROS のセットアップ

[Windows (binary)](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html) の手順にしたがう。


## その他ライブラリ

examples のビルドには numpy が必要だが、python の site-packages にインストールされている必要がある。

```
pip install numpy
```

## VSCode の場合

- ワークスペースファイル `ros2-win-examples.code-workspace` で開く。
- ワークスペースの推奨パッケージを有効化する。
- `Ctrl + Shift + P` で `Python: Create Envhumblement...` で venv 環境を作成。Pythonバージョンはhumbleの場合は3.8.xを選択する。requirements.txt で必要なパッケージをインストールする。
- `ターミナル(T)` -> `タスクの実行...` -> `build` でビルド実行。

## コマンドラインの場合

### venv 環境の作成

特にPythonのROS推奨以外のバージョンがインストールされている場合に、確実に推奨バージョン (3.8.3) が用いられるようにする。

```
python -m venv .venv --system-site-packages
```

### Build

Run following command on "Developer console of Visual Studio":

```
. C:/dev/ros2_humble/local_setup.ps1
. .venv/Scripts/Activate.ps1
colcon build --cmake-args -DPython3_FIND_VIRTUALENV="ONLY" --event-handlers desktop_notification-
```
