---
title: '手順 1: pyodbc Python 開発環境の構成 |Microsoft Docs'
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f588174ea80677066628cb3e756d7c38bd42fba
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2018
ms.locfileid: "42784449"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>手順 1: pyodbc Python 開発用に開発環境を構成する

## <a name="windows"></a>Windows  
Python の Windows で pyodbc を使用して SQL Database に接続します。
  
1. **Python インストーラーをダウンロード**します。  
  コンピューターに Python があるない場合はインストールします。 移動して、 [Python をダウンロードできるページ](https://www.python.org/downloads/windows/)し、適切なインストーラーをダウンロードします。 たとえば、64 ビット コンピューターの場合は、Python 2.7 または 3.7 (x 64) インストーラーをダウンロードします。  
  
2. **Python をインストール**します。  インストーラーがダウンロードされると、次の手順を実行します。 をします。 インストーラーを起動するファイルをダブルクリックします。 B. 言語を選択し、条項に同意します。 c. 画面の指示に従って、Python は、コンピューターにインストールする必要があります。 d. 移動して、Python がインストールされていることを確認する`C:\Python27`または`C:\Python37`実行`python -V`または`py -V`(3.x) の 
      
3. [**Microsoft ODBC Driver for SQL Server on Windows をインストール**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)します。
  
4. **管理者として cmd.exe を開きます。**     

5. **Pip、Python パッケージ マネージャーを使用して pyodbc をインストール**(置換`C:\Python27\Scripts`をインストールされている Python パス)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Python で pyodbc を使用して SQL Database に接続します。
  
1. **ターミナルを開く**  

2. [**Microsoft ODBC Driver for SQL Server on Linux をインストール**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。

3.  **Pyodbc をインストールします。**  
```  
> sudo -H pip install pyodbc
```
