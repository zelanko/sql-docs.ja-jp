---
title: 手順 1:pyodbc Python 開発環境を構成する |Microsoft Docs
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dd2063a527d782833f2abfcbd635de30aa27117
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926775"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>手順 1:pyodbc Python 開発用に開発環境を構成する

## <a name="windows"></a>Windows  
Windows 上で Python - pyodbc を使用して SQL Database に接続します。
  
1. **Python インストーラーをダウンロードします**。  
  コンピューターに Python がインストールされていない場合は、インストールします。 [Python ダウンロード ページ](https://www.python.org/downloads/windows/)にアクセスし、適切なインストーラーをダウンロードします。 たとえば、64 ビットのコンピューターを使用している場合、Python 2.7 または 3.7 (x64) インストーラーをダウンロードします。  
  
2. **Python をインストール**します。  インストーラーをダウンロードしたら、次の手順に従います。a. ファイルをダブルクリックしてインストーラーを起動します。 b. 言語を選択し、使用条件に同意します。 c. 画面の指示に従うと、コンピューターに Python がインストールされます。 d. Python がインストールされていることを確認するには、`C:\Python27` または `C:\Python37` に移動し、`python -V` または `py -V` (3.x の場合) を実行します。 
      
3. [**Microsoft ODBC Driver for SQL Server on Windows をインストール**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)します。
  
4. **管理者として cmd.exe を開きます**。     

5. **pip - Python パッケージ マネージャーを使用して pyodbc をインストールします** (`C:\Python27\Scripts` をインストール済みの Python パスに置き換えます)。
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Python - pyodbc を使用して SQL Database に接続します。
  
1. **ターミナルを開きます**  

2. [**Microsoft ODBC Driver for SQL Server on Linux をインストール**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。

3.  **pyodbc をインストールします**。  
```  
> sudo -H pip install pyodbc
```
