---
title: ODBC ビジュアル フォックスプロ セットアップ ダイアログ ボックス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], installing
- FoxPro ODBC driver [ODBC], installing
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef7ac702a69342833c6dfffa0ffc9cdd0ac2857e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298082"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>ODBC Visual FoxPro セットアップ ダイアログ ボックス
**ODBC ビジュアル フォックス プロのセットアップ**ダイアログ ボックスを追加またはビジュアル フォックスプロデータ ソースを変更することができます。  
  
 ドライバをダウンロードするには、[ビジュアル フォックスプロ ODBC ドライバのダウンロード サイト](https://go.microsoft.com/fwlink/?LinkId=121318)を参照してください。  
  
## <a name="dialog-box-options"></a>ダイアログ ボックス オプション  
 **データ ソース名**  
 データ ソースに使用する名前を入力します。  
  
 **説明**  
 データ ソースの説明を入力します。  
  
 **データベースの種類**  
 データ ソースの接続先となるデータベースの種類を選択できます。  
  
 **ビジュアルフォックスプロデータベース (.DBC)**  
 データ ソースが Visual FoxPro データベース (.dbc ファイル) と[、データベース](../../odbc/microsoft/visual-foxpro-terminology.md)内のすべてのテーブルとローカル ビューに接続することを指定します。  
  
 **フリーテーブルディレクトリ**  
 データ ソースが[空きテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリに接続することを指定します。 同じディレクトリ内の[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)テーブルは[、SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)や[SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)などの ODBC カタログ関数によって無視されます。 データベース テーブルにアクセスするには、 SQL 実行および[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)を介して送信される[SQL](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) SELECT ステートメントを使用します。  
  
 **パス**  
 データ ソースが接続する空きテーブルのデータベースまたはディレクトリのパスと名前を表示します。  
  
 **参照**  
 データ ソースに接続するデータベースまたはディレクトリをシステムおよびネットワークで検索できます。  
  
 **[オプション]**  
 ダイアログ ボックスを展開して、Visual FoxPro ODBC ドライバーのオプションを設定できるようにします。  
  
## <a name="driver"></a>Driver  
 **照合順序**  
 フィールドが並べ替えられる順序。 デフォルトのシーケンスは、オペレーティング・システムの言語バージョンでサポートされているシーケンスを反映しています。 サポートされる照合シーケンスのリストについては[、SET COLLATE](../../odbc/microsoft/set-collate-command.md)を参照してください。  
  
 **[Exclusive]**  
 このチェック ボックスをオンにすると、データ ソースを使用してデータにアクセスするときに、ドライバーは Visual FoxPro データベースを排他的に開きます。 データベースを排他的に開いている間は、他のユーザーはデータベースまたはデータベース内のテーブルにアクセスできません。 排他的に開かれたデータベース内のテーブルは SHARED として開かれます。 テーブルを排他的に開くには[、SET EXCLUSIVE](../../odbc/microsoft/set-exclusive-command.md)コマンドを使用します。 このチェック ボックスは、[**データベースの種類]** が **[テーブルの空きディレクトリ**] に設定されている場合は無効になります。  
  
 **Null**  
 ALTER TABLE および CREATE TABLE で作成された列で NULL 値を許可するかどうかを決定します。 NULL を設定すると、INSERT - SQL は、INSERT - SQL.値節。 NULL が OFF の場合はブランクが挿入されます。 渡された接続文字列を使用して、次のコードのようにこのオプションを制御することもできます。  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Deleted**  
 削除済みとしてマークされた行を返すかどうかを指定します。 渡された接続文字列を使用して、次のコードのようにこのオプションを制御することもできます。  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **バックグラウンドでのデータのフェッチ**  
 レコードをバックグラウンドでフェッチするか (プログレッシブフェッチ)、またはアプリケーションが結果セット内のすべてのレコードがフェッチされるまで待機するかを決定します。
