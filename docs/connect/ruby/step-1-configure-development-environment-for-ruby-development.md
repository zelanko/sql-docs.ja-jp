---
title: "手順 1: Ruby 開発のための開発環境の構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ruby
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d722d1eed21162d5e076f5dfdfc3a2f18787f42e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>手順 1: Ruby 開発のための開発環境を構成します。
SQL Server の Ruby ドライバーを使用してアプリケーションを開発するために、前提条件と開発環境を構成する必要があります。    
  
Ruby ドライバーが SQL Server と Azure SQL データベースで既定で有効になっている TDS プロトコルを使用することに注意してください。  追加の構成は必要ありません。  
  
  
## <a name="windows"></a>Windows  
  
1.  **ルビのインストーラーをダウンロードします。**  
コンピューターには、インストールしてください Ruby はありません。 場合、 新しい ruby ユーザー Ruby 2.2.X インストーラーを使用することをお勧めします。 これらは、安定した言語と互換性があり、更新済みであるパッケージ (gems) の広範な一覧を提供します。 移動、 [Ruby ダウンロード ページ](http://rubyinstaller.org/downloads/)し、適切な 2.1.x インストーラーをダウンロードします。 例に、64 ビット コンピューター上にいる場合は、Ruby 2.1.6 (x64) のインストーラーをダウンロードします。   
  
2.  **ルビをインストールします。**  
インストーラーをダウンロードすると、次の操作を行います。  
a. ファイルをダブルクリックして、インストーラーを起動します。  
b. 使用言語を選択し、条項に同意します。  
c.  インストール設定画面で、このインストールにより Ruby パスと関連付ける .rb と .rbw ファイルに両方のルビの追加の実行可能ファイルの横にあるチェック ボックスを選択します。  
  
3.  **ルビの開発キットをダウンロードします。**  
RubyInstaller ページから開発キットをダウンロードします。  
  
4.  **ルビの開発キットをインストールします。**  
ダウンロードが完了したら、次の操作を行います。  
a. ファイルをダブルクリックします。 ファイルを抽出する場所を求められます。  
b. [...] ボタンをクリックし、"C:\DevKit"を選択します。 「新しいフォルダーの作成」をクリックして、最初このフォルダーを作成する必要があります。  
c. "OK"し、「抽出」、ファイルを抽出する をクリックします。  
  
5. **Cmd.exe を開きます**  
  
6. **ルビの開発キットを初期化します。**  
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
  
1. **開いているターミナル**  
  
2. **Ruby バージョン マネージャー (rvm) および前提条件をインストールします。**  
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
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;バージョン 2.3.0 を実行している最後のコマンドの出力を示すことを確認します。  
  
4.  **インストール、FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **TinyTDS をインストールします。**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Mac OS X は既にプレインストールされて、Ruby、OS が依存関係を持つように注意してください。    
  
1.  **開いているターミナル**  
  
2. **Homebrew パッケージ マネージャーをインストールします。**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **インストール、FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **TinyTDS gem をインストールします。**  
```  
> gem install tiny_tds  
```

