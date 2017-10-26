---
title: "パスの SET コマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 490fefba9286a970b21014c66d681426703978fc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="set-path-command"></a>SET PATH コマンド
ファイル検索用のパスを指定します。 ドライバー固有の情報は、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>引数  
 [*パス*]  
 Visual FoxPro を検索するディレクトリを指定します。 コンマまたはセミコロンを使用して、ディレクトリを区切ります。  
  
## <a name="remarks"></a>解説  
 パスの設定では、ストアド プロシージャ内で呼び出すことができるその他の Visual FoxPro プログラムの検索パスを指定することができます。 パスの設定では、接続の指定したデータ ソースのパスは変更されません。  
  
 発行設定パスなし*パス*を既定のディレクトリまたはフォルダーへのパスを復元します。  
  
## <a name="driver-remarks"></a>ドライバーの解説  
 ストアド プロシージャにパスの設定を発行した場合は、次の関数やコマンドによって無視されます。  
  
-   カタログ関数をなど[SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)と[SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)は、新しいパスを無視し、内のデータ ソースによって指定されたパスの参照は引き続き[SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md)または[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)です。  
  
-   SELECT、INSERT、UPDATE、DELETE、および CREATE TABLE などのコマンドは、新しいパスを無視して引き続き内のデータ ソースによって指定されたパスを参照**SQLPrepare**または**SQLExecDirect**です。  
  
 ストアド プロシージャにパスの設定を発行して、元の状態にパスを設定しないで、その後、その他のデータベースへの接続は (パスの設定はデータのセッションのスコープではない) ため、新しいパスを使用します。  
  
 作成、選択、またはデータ ソースで指定されている以外のディレクトリ内のテーブルを更新する場合は、コマンドにファイルの完全なパスを指定します。  
  
## <a name="see-also"></a>参照  
 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (Visual FoxPro ODBC ドライバー)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (Visual FoxPro ODBC ドライバー)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (Visual FoxPro ODBC ドライバー)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)

