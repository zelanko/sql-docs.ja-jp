---
title: "手順 1: pymssql Python 開発環境の構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: python
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0a1932b41ada3469deed6d36a3c68c3827687cc5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>手順 1: pymssql Python 開発用の開発環境を構成します。
SQL Server 用 Python ドライバーを使用してアプリケーションを開発するために、前提条件と開発環境を構成する必要があります。    
  
Python SQL ドライバーが既定では SQL Server と Azure SQL データベースで有効になっている TDS プロトコルを使用することに注意してください。  追加の構成は必要ありません。  
  
## <a name="windows"></a>Windows  
  
1. **Python ランタイムをインストールおよびパッケージ マネージャーの pip**  
a. 移動して[python.org](https://www.python.org/downloads/)  
b. Windows インストーラー msi の適切なリンクをクリックします。   
c. 1 回ダウンロードした実行 Python ランタイムをインストールする msi  
  
2. **Pymssql モジュールをダウンロード**から[ここ](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    正しい whl ファイルを選択することを確認してください。  例: 64 ビット コンピューターで Python 2.7 を使用している場合は選択: pymssql‑2.1.1‑cp27‑none‑win_amd64.whl です。 ダウンロードしたら、.whl ファイルの配置、c:/Python27 フォルダーです。  
      
3. **Cmd.exe を開きます**  
  
4. **Pymssql モジュールをインストールします。**     
    たとえば、64 ビット コンピューターで Python 2.7 を使用するいるとします。  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Python ランタイムをインストールおよびパッケージ マネージャーの pip** Ubuntu のほとんどのディストリビューションに Python があらかじめインストールされています。  コンピューターでは、python をインストールすることはありません場合、入手できますかダウンロードからソース陥らない[python.org](https://www.python.org/downloads/)ローカルでビルドし、パッケージ マネージャーを使用することができます。  
```  
> sudo apt-get install python   
```  
  
2.  **開いているターミナル**  
  
3.  **Pymssql モジュールとの依存関係をインストールします。**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Python ランタイムをインストールおよびパッケージ マネージャーの pip**  
a. 移動して[python.org](https://www.python.org/downloads/)  
b. Mac インストーラー パッケージの適切なリンクをクリックします。   
c. 1 回ダウンロードした実行 Python ランタイムをインストールするパッケージ  
  
2.  **開いているターミナル**  
  
3. **Homebrew パッケージ マネージャーをインストールします。**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **FreeTDS モジュールをインストールします。**  
```  
> brew install FreeTDS  
```  
  
5.  **Pymssql モジュールをインストールします。**  
```  
> sudo -H pip install pymssql  
```

