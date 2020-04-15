---
title: パスコマンドの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e44093c3ea18bc995264a8974726f5af0abe3b3a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300822"
---
# <a name="set-path-command"></a>SET PATH コマンド
ファイル検索のパスを指定します。 ドライバ固有の情報については、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>引数  
 [*パス*]  
 検索するディレクトリを指定します。 ディレクトリを区切るには、カンマまたはセミコロンを使用します。  
  
## <a name="remarks"></a>解説  
 SET PATH を使用すると、ストアド プロシージャ内で呼び出すことができる他の Visual FoxPro プログラムの検索パスを指定できます。 SET PATH は、接続に指定したデータ ソースのパスを変更しません。  
  
 パスをデフォルトのディレクトリまたはフォルダに復元するには、*パス*を指定せずにパスを設定します。  
  
## <a name="driver-remarks"></a>ドライバの解説  
 ストアド プロシージャで SET PATH を発行すると、次の関数およびコマンドによって無視されます。  
  
-   [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)や[SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)などのカタログ関数は、新しいパスを無視し[、SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md)または[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)でデータ ソースによって指定されたパスを参照し続けます。  
  
-   SELECT、挿入、更新、削除、およびテーブルの作成などのコマンドは、新しいパスを無視し **、SQLPrepare**または**SQLExecDirect**でデータ ソースによって指定されたパスを参照し続けます。  
  
 ストアド プロシージャで SET PATH を発行し、その後パスを元の状態に戻さないと、データベースへの他の接続では新しいパスが使用されます (SET PATH はデータ セッションのスコープを指定しないため)。  
  
 データ ソースで指定されている以外のディレクトリのテーブルを作成、選択、または更新する場合は、コマンドを使用してファイルの完全パスを指定します。  
  
## <a name="see-also"></a>参照  
 [ODBC ビジュアル フォックスプロのセットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQL 列 (ビジュアル フォックスプロ ODBC ドライバー)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [コネクト (ビジュアル フォックスプロ ODBC ドライバー)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (Visual FoxPro ODBC ドライバー)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
