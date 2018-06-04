# 道路診断アプリケーション

## 動作環境
* python3.6

## インストールするべきライブラリ（実行時のバージョン）
* scipy (0.18.1)
* numpy (1.11.3)
* pandas (0.19.2)

# 使用方法
1. 凸凹の大きさ計算。インプットデータとしてD4C~の公用車走行データを使用する。
```
$ python src/fftRoadAnalytics.py "inputfile name" "output directory name"
```

### ここでは以下のようなcsvが作成される。
インデックス番号、車両ID、日時、凸凹の大きさ、凸凹の大きさ(non use)、緯度、経度
```
0,aizu_BL-01_10,2017-01-12 23:39:30.337,5761.866505649465,25.749000314623117,37.50027,139.891819
1,aizu_BL-01_10,2017-01-12 23:39:32.337,4302.1897377746645,16.477000101003796,37.50027,139.891875
2,aizu_BL-01_10,2017-01-12 23:39:34.337,2948.9170512897545,15.745000100228935,37.500265999999996,139.891966
```

2. 作成した凸凹の大きさデータから、地図上にマッピングする元のデータを作成する。
```
$ python src/road_range2.py "inputfile name"
```
test.csvという名前で保存される。

road_range2.pyのパラメータ
- TH = 3000
    - 1で作成した凸凹のの大きさにより、凹凸がひどいかそうでないかを判断する。
- L = 50
    - 可視化をするために格子状にマップを分割して、赤色をそれぞれの格子につけるようにしているが、その時の各格子の大きさについて決定するためにここのパラメータをいじってください。単位はメートルです。

3. htmlファイルをブラウザで開き、そこで読み取るファイルとして先ほど作成したtest.csvを選択する。

