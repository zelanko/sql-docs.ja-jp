---
title: "手順 1: pyodbc Python 開発環境の構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3910f1f3053e0dee053b16575e5447474c75bf40
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>手順 1: pyodbc Python 開発用の開発環境を構成します。

## <a name="windows"></a>Windows  
Python - pyodbc on Windows を使用して SQL データベースに接続します。
  
1. **Python のインストーラーをダウンロードします。**  
  場合は、コンピューターには、Python をインストールしてくださいはありません。 移動、 [Python ダウンロード ページ](https://www.python.org/downloads/windows/) し、適切なインストーラーをダウンロードします。 例に 64 ビット コンピューター上にいる場合は、Python 2.7 または 3.5 (x64) のインストーラーをダウンロードします。  
  
2. **Python をインストール**インストーラーをダウンロードすると、次の操作: します。 ファイルをダブルクリックして、インストーラーを起動します。 b. 使用言語を選択し、条項に同意します。 c. 画面の指示に従って、Python は、コンピューターにインストールする必要があります。 d. 確認できますが Python が C:\Python27 または C:\Python35 に移動してインストールされているし、python-v または py-v (3.x) の実行 
      
3. [**Microsoft ODBC Driver をインストールします。**](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)
  
4. **管理者として cmd.exe を開きます**     

5. **Pip に使用して pyodbc Python パッケージ マネージャーをインストールします。**
```  
> cd C:\Python27\Scripts>  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Python - Ubuntu と Red Hat pyodbc を使用して SQL データベースに接続します。
  
1. **開いているターミナル**  

2. **Linux 用 Microsoft ODBC Driver 13 をインストール**Ubuntu 15.04 用 + 
``` 
> sudo su  
> wget https://gallery.technet.microsoft.com/ODBC-Driver-13-for-Ubuntu-b87369f0/file/154097/2/installodbc.sh  
> sh installodbc.sh  
```   

  Red Hat 6、7 の 
``` 
> sudo su 
> wget https://gallery.technet.microsoft.com/ODBC-Driver-13-for-SQL-8d067754/file/153653/4/install.sh 
> sh install.sh 
```  
  
3.  **Pyodbc をインストールします。**  
```  
> sudo -H pip install pyodbc
```

