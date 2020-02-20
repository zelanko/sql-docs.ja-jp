---
title: 手順 1:Ruby 開発用に開発環境を構成する | Microsoft Docs
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
ms.openlocfilehash: 38af92d3cb0354bc4b75131a349f6a1c26e90490
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67992464"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>手順 1:Ruby 開発用に開発環境を構成する
SQL Server 用の Ruby ドライバーを使用してアプリケーションを開発するには、前提条件を使用して開発環境を構成する必要があります。    
  
Ruby ドライバーでは TDS プロトコルが使用されていることに注意してください。これは SQL Server と Azure SQL Database で既定で有効になっています。  追加の構成は不要です。  
  
  
## <a name="windows"></a>Windows  
  
1.  **Ruby インストーラーをダウンロードします**。  
コンピューターに Ruby がインストールされていない場合は、インストールしてください。 初めて Ruby を使用する場合は、Ruby 2.2. X インストーラーを使用することをお勧めします。 これにより、安定した言語と、互換性のある更新済みのパッケージ (gem) の広範囲な一覧が提供されます。 [Ruby ダウンロード ページ](https://rubyinstaller.org/downloads/)にアクセスし、適切な 2.1.x インストーラーをダウンロードします。 たとえば、64 ビットのコンピューターを使用している場合、Ruby 2.1.6 (x64) インストーラーをダウンロードします。   
  
2.  **Ruby をインストールします**。  
インストーラーをダウンロードしたら、次の手順に従います。  
a. ファイルをダブルクリックしてインストーラーを起動します。  
b. 言語を選択し、使用条件に同意します。  
c.  インストールの設定画面で、[Add Ruby executables to your PATH]\(Ruby の実行可能ファイルを PATH に追加する\) と [Associate .rb and .rbw files with this Ruby installation]\(.rb ファイルと .rbw ファイルをこの Ruby インストールに関連付ける\) の横の両方のチェック ボックスをオンにします。  
  
3.  **Ruby DevKit をダウンロードします**。  
RubyInstaller ページから DevKit をダウンロードします。  
  
4.  **Ruby DevKit をインストールします**。  
ダウンロードが完了したら、次の手順に従います。  
a. ファイルをダブルクリックします。 ファイルの抽出先を確認するメッセージが表示されます。  
b. [...] ボタンをクリックし、[C:\DevKit] を選択します。 このフォルダーは、[新しいフォルダーの作成] をクリックして最初に作成する必要のある場合があります。  
c. [OK] をクリックし、[抽出] をクリックしてファイルを抽出します。  
  
5. **Cmd.exe を開きます**  
  
6. **Ruby DevKit を初期化します**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **TinyTDS gem をインストールします**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **ターミナルを開きます**  
  
2. **Ruby バージョン マネージャー (rvm) と前提条件をインストールします**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **rvm を使用して Ruby をインストールします**  
たとえば、Ruby バージョン 2.3.0 をインストールします。  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;最後のコマンドの出力が、バージョン 2.3.0 が実行されていることを確実に示すようにします。  
  
4.  **FreeTDS をインストールします**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **TinyTDS をインストールします**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
OS には依存関係があるため、Mac OS X には既に Ruby が事前インストールされていることに注意してください。    
  
1.  **ターミナルを開きます**  
  
2. **Homebrew パッケージ マネージャーをインストールします**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **FreeTDS をインストールします**  
```  
> brew install FreeTDS  
```  
  
4.  **TinyTDS gem をインストールします**  
```  
> gem install tiny_tds  
```
