---
title: '手順 1: pymssql Python 開発環境の構成 |Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 623b4bf9a88031cf891e88f75c30b06716bb27ff
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51605022"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>ステップ 1: pymssql Python 開発用に開発環境を構成する
SQL Server 用 Python ドライバーを使用してアプリケーションを開発するために、前提条件、開発環境を構成する必要があります。    
  
Python SQL ドライバーが SQL Server と Azure SQL Database での既定で有効になっている TDS プロトコルを使用することに注意してください。  追加の構成は必要ありません。  
  
## <a name="windows"></a>Windows  
  
1. **Python ランタイムをインストールし、pip パッケージ マネージャー**  
A. 移動して[python.org](https://www.python.org/downloads/)  
B. 適切な Windows インストーラーの msi リンクをクリックします。   
c. 1 回ダウンロードした Python ランタイムをインストールする msi を実行  
  
2. **Pymssql モジュールをダウンロード**から[ここ](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    正しい whl ファイルを選択することを確認します。  例: 64 ビット コンピューター上の Python 2.7 を使用している場合は選択: pymssql‑2.1.1‑cp27‑none‑win_amd64.whl します。 ダウンロードすると、c:/python27 フォルダーに配置 .whl ファイル。  
      
3. **Cmd.exe を開きます**  
  
4. **Pymssql モジュールをインストールします。**     
    たとえば、64 ビット コンピューター上の Python 2.7 を使用するいるとします。  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Python ランタイムをインストールし、pip パッケージ マネージャー** Python は Ubuntu のほとんどのディストリビューションにプレインストールされています。  ソース ターボール ダウンロードするかを取得することができます、コンピューターがインストールされている python を持たない場合[python.org](https://www.python.org/downloads/)とローカルでビルドまたはパッケージ マネージャーを使用することができます。  
```  
> sudo apt-get install python   
```  
  
2.  **ターミナルを開く**  
  
3.  **Pymssql モジュールをインストールして、依存関係**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Python ランタイムをインストールし、pip パッケージ マネージャー**  
A. 移動して[python.org](https://www.python.org/downloads/)  
B. 適切な Mac インストーラー パッケージ リンクをクリックします。   
c. 1 回ダウンロードした Python ランタイムをインストールするパッケージを実行  
  
2.  **ターミナルを開く**  
  
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
