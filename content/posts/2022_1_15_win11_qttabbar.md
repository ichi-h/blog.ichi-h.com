---
author: 'ichi'
date: 2022-01-14
lastmod: 2022-01-18
linktitle: Windows 11にQTTabBarをインストールする方法
title: Windows 11にQTTabBarをインストールする方法
weight: 10
url: /posts/win11_qttabbar
tags: ['life', 'windows11']
hideWordCount: true
hideReadingTime: true
draft: false
---

## はじめに

Windows11になってからエクスプローラーのUIが変更されたことで、QTTabBarのインストールが簡単にはできなくなりました。ので、今回はそのやり方の共有となります。

## 注意

<span class="positive">この方法ではレジストリに対して一時的に変更を加えます。2021年12月末に検証した際は成功しましたが、今後のWindowsのアップデートによっては利用できなくなる可能性があります。</span>

## QTTabBarとは？

簡単に言えば、<u>エクスプローラーにタブ機能を追加できる拡張機能</u>です。  
他にもいろいろと便利機能があるのですが、それに関してはまた別の機会に。

<div class="link-card"><div class="link-card-thumbnail"><a href="http://qttabbar-ja.wikidot.com/" class="link-card-thumbnail-link" target="_blank" rel="noopener noreferrer"><img class="link-card-thumb-image" src="" alt=""></a></div><div class="link-card-content"><div class="link-card-title"><a href="http://qttabbar-ja.wikidot.com/" target="_blank" rel="noopener noreferrer">QTTabBar - QuizoApps</a></div><div class="link-card-excerpt"></div></div><div class="link-card-footer"><a href="http://qttabbar-ja.wikidot.com/" target="_blank" rel="noopener noreferrer"><img src="https://www.google.com/s2/favicons?domain=http://qttabbar-ja.wikidot.com/" alt="">qttabbar-ja.wikidot.com</a></div></div>


## やり方

### 1. QTTabBarのインストール

はじめにQTTabBarのインストールを行ってください。私は窓の社さんのものを利用しました。

<div class="link-card"><div class="link-card-thumbnail"><a href="https://forest.watch.impress.co.jp/library/software/qttabbar/" class="link-card-thumbnail-link" target="_blank" rel="noopener noreferrer"><img class="link-card-thumb-image" src="https://forest.watch.impress.co.jp/library/img/review/10390/qttabbar.jpg" alt=""></a></div><div class="link-card-content"><div class="link-card-title"><a href="https://forest.watch.impress.co.jp/library/software/qttabbar/" target="_blank" rel="noopener noreferrer">「QTTabBar」エクスプローラーにタブ切り替え機能を追加できるツールバー - 窓の杜</a></div><div class="link-card-excerpt">QTTabBarのダウンロードはこちら 　エクスプローラーのツールバーにタブ切り替え機能を追加し、1つのウィンドウで複数のフォルダーを開けるようにするソフト。インストール後、エクスプローラーの［表示］...</div></div><div class="link-card-footer"><a href="https://forest.watch.impress.co.jp/library/software/qttabbar/" target="_blank" rel="noopener noreferrer"><img src="https://www.google.com/s2/favicons?domain=https://forest.watch.impress.co.jp/library/software/qttabbar/" alt="">forest.watch.impress.co.jp</a></div></div>

### 1. エクスプローラーのUIをWindows 10に戻す

Windows 11では、エクスプローラーの上部にあったメニュー的なもの（リボン）から「オプション」が削除されたため、このままではQTTabBarの機能を有効にすることができません。  
なので、まずはエクスプローラーを旧版のものに戻します。

はじめに、Win + Rコマンドから「ファイル名を指定して実行」を立ち上げ、「powershell」を入力してPowerShellを起動します。

その後、以下のコマンドを貼り付けて実行してください。  
（ここでレジストリを操作しますが、最後に元に戻せます）

```powershell
reg.exe add "HKCU\Software\Classes\CLSID\{d93ed569-3b3e-4bff-8355-3c44f6a52bb5}\InprocServer32" /f /ve
```

その後、<u>PCの再起動</u>を行うことで、エクスプローラーのリボンにオプションが表示されるようになります。

### 2. QTTabBarを有効にする

あとは通常のQTTabBarの設定と同じです。  
エクスプローラーのオプションから「QT タブ バー」を有効にすることで、エクスプローラーにタブが表示されます。

### 3. エクスプローラーのUIを元に戻す

エクスプローラーのUIを元に戻す場合は、PowerShellにて以下のコマンドを実行し、PCを再起動すれば元に戻ります。  
元に戻したとしても、QTTabBarは引き続き使用することができます。

```powershell
reg.exe delete "HKCU\Software\Classes\CLSID\{d93ed569-3b3e-4bff-8355-3c44f6a52bb5}" /f
```

## おまけ

私のQTTabBarの設定を共有いたします。  
ゴリゴリにチューニングしているわけではありませんが、直感的に使える設定にはなっていると思いますので、ぜひお試しください。  
リンクはGoogle Driveへとつながります。

<a class="border" href="https://drive.google.com/file/d/1qPnj13bAMdqzYFj2f-VAOCPd4EXlOIzh/view?usp=sharing" target="_blank" rel="noopener noreferrer">ダウンロード</a>

設定を読み込む場合は、タブバーを右クリックするか、Alt + Oのショートカットキーから「QTTabBar のオプション」を開き、「全般 -> 管理の設定 -> ファイルからインポートする」をクリックし、ダウンロードしたファイルを選択してください。

## 参考

- <a class="border" href="https://starmint.net/windows11-explorer-ribbon-old-style.html" target="_blank" rel="noopener noreferrer">【Windows 11】エクスプローラーのリボンをWin10の仕様に戻す方法 | スターミント</a>
