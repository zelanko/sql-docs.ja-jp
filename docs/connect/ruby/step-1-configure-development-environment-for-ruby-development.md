---
title: 'ステップ 1: Ruby 開発用に開発環境を構成する | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ff03ce6ec79aede2e056f0154836e77970af9c50
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800831"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>ステップ 1: Ruby 開発用に開発環境を構成する
SQL Server 用 Ruby ドライバーを使用してアプリケーションを開発するために、前提条件、開発環境を構成する必要があります。    
  
Ruby Driver が SQL Server と Azure SQL Database での既定で有効になっている TDS プロトコルを使用することに注意してください。  追加の構成は必要ありません。  
  
  
## <a name="windows"></a>Windows  
  
1.  **Ruby のインストーラーをダウンロードします。**  
場合は、コンピューターには、Ruby をインストールしてくださいはありません。 新しい ruby ユーザーは、Ruby 2.2.X インストーラーの使用をお勧めします。 これらは、安定した言語とは互換性があり、更新されたパッケージ (gem) の広範な一覧を提供します。 移動、 [Ruby のダウンロード ページ](https://rubyinstaller.org/downloads/)し、適切な 2.1.x がインストールされたインストーラーをダウンロードします。 例に、64 ビット コンピューター上にいる場合は、Ruby 2.1.6 (x 64) インストーラーをダウンロードします。   
  
2.  **Ruby をインストールします。**  
インストーラーがダウンロードされると、次の操作を行います。  
A. インストーラーを起動するファイルをダブルクリックします。  
B. 言語を選択し、条項に同意します。  
c.  インストールの設定画面で、この Ruby のインストール パスと関連付ける .rb と .rbw ファイルに両方のルビの追加の実行可能ファイルの横にあるチェック ボックスを選択します。  
  
3.  **Ruby DevKit をダウンロードします。**  
DevKit を RubyInstaller ページからダウンロードします。  
  
4.  **DevKit の Ruby のインストールします。**  
ダウンロードが完了したら後、は、次の操作を行います。  
A. ファイルをダブルクリックします。 ファイルを抽出する場所を求められます。  
B. [...] ボタンをクリックし、"C:\DevKit"を選択します。 "新しいフォルダーの作成 をクリックして、最初このフォルダーを作成する必要があります。  
c. ファイルを抽出する"OK"と「展開」をクリックします。  
  
5. **Cmd.exe を開きます**  
  
6. **DevKit の Ruby の初期化します。**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **TinyTDS gem をインストールします。**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **ターミナルを開く**  
  
2. **Ruby のバージョン マネージャー (rvm) と前提条件をインストールします。**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Rvm を使用して、Ruby をインストールするには**  
たとえば、Ruby のバージョン 2.3.0 をインストールします。  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;最後のコマンドの出力がバージョン 2.3.0 を実行していることを示すことを確認します。  
  
4.  **FreeTDS をインストールします**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **TinyTDS をインストールします。**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Mac OS X に既にある Ruby を事前にインストール、OS は、依存関係を持つように注意してください。    
  
1.  **ターミナルを開く**  
  
2. **Homebrew パッケージ マネージャーをインストールします。**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **FreeTDS をインストールします**  
```  
> brew install FreeTDS  
```  
  
4.  **TinyTDS gem をインストールします。**  
```  
> gem install tiny_tds  
```
