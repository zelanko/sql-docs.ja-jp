---
title: 手順 1:pymssql Python 開発環境を構成する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3310f268bf04b015c5f80cd08b2ae3909fd3a5c2
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926805"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>手順 1:pymssql Python 開発用に開発環境を構成する
SQL Server 用の Python ドライバーを使用してアプリケーションを開発するには、前提条件に従ってご自分の開発環境を構成する必要があります。    
  
なお、Python SQL ドライバーでは TDS プロトコルを使用しています。これは SQL Server と Azure SQL Database で既定で有効になっています。  追加の構成は不要です。  
  
## <a name="windows"></a>Windows  
  
1. **Python ランタイムと pip パッケージ マネージャーをインストールします**  
a. [python.org](https://www.python.org/downloads/) に移動します。  
b. 適切な Windows インストーラーの msi リンクをクリックします。   
c. ダウンロードが完了したら、msi を実行して Python ランタイムをインストールします。  
  
2. [ここから](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql) **pymssql モジュールをダウンロードします。**  
  
    正しい whl ファイルを選択していることをご確認ください。  例:64 ビット コンピューター上で Python 2.7 を使用している場合は、pymssql‑2.1.1‑cp27‑none‑win_amd64.whl を選択します。 .whl ファイルをダウンロードしたら、C:/Python27 フォルダーに配置します。  
      
3. **cmd.exe を開きます**  
  
4. **pymssql モジュールをインストールします**     
    たとえば、64 ビット コンピューターで Python 2.7 を使用している場合は、次のようになります。  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Python ランタイムと pip パッケージ マネージャーをインストールします** Python は Ubuntu のほとんどのディストリビューションにあらかじめインストールされています。  お使いのコンピューターに python がインストールされていない場合は、[python.org](https://www.python.org/downloads/) からソースの tar ファイルをダウンロードしてローカルでビルドするか、次のようにパッケージ マネージャーを使用できます。  
```  
> sudo apt-get install python   
```  
  
2.  **ターミナルを開きます**  
  
3.  **pymssql モジュールと依存関係をインストールします**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Python ランタイムと pip パッケージ マネージャーをインストールします**  
a. [python.org](https://www.python.org/downloads/) に移動します。  
b. 適切な Mac インストーラーの pkg リンクをクリックします。   
c. ダウンロードが完了したら、pkg を実行して Python ランタイムをインストールします。  
  
2.  **ターミナルを開きます**  
  
3. **Homebrew パッケージ マネージャーをインストールします**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **FreeTDS モジュールをインストールします**  
```  
> brew install FreeTDS  
```  
  
5.  **pymssql モジュールをインストールします**  
```  
> sudo -H pip install pymssql  
```
