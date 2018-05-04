---
title: ODBC Visual FoxPro セットアップ ダイアログ ボックス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], installing
- FoxPro ODBC driver [ODBC], installing
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 516a9412a3a879421fccba9af79af3d2730acab4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>ODBC Visual FoxPro セットアップ ダイアログ ボックス
**ODBC Visual FoxPro セットアップ**ダイアログ ボックスでは、Visual FoxPro データ ソースの変更を追加することができます。  
  
 ドライバーをダウンロードするを参照してください。 [Visual FoxPro ODBC ドライバーのダウンロード サイト](http://go.microsoft.com/fwlink/?LinkId=121318)です。  
  
## <a name="dialog-box-options"></a>ダイアログ ボックスのオプション  
 **データ ソース名**  
 データ ソースを使用する名前を入力します。  
  
 **Description**  
 データ ソースの説明を入力します。  
  
 **データベースの種類**  
 データ ソースに接続データベースの種類を選択することができます。  
  
 **Visual FoxPro データベース (です。DBC)**  
 Visual FoxPro にデータ ソースを接続することを示す[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)(.dbc ファイル) とすべてのテーブルおよびデータベースのローカルのビューにします。  
  
 **無料のテーブルのディレクトリ**  
 ディレクトリに、データ ソースを接続することを示す[テーブルの空き](../../odbc/microsoft/visual-foxpro-terminology.md)です。 どの[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)同じディレクトリ内のテーブルでは無視されます ODBC カタログ関数など[SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)または[SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)です。 送信される SQL SELECT ステートメントを使用してデータベース テーブルにアクセスできる[SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md)と[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)です。  
  
 **[パス]**  
 データベースまたはデータ ソースに接続する無料のテーブルのディレクトリの名前とパスを表示します。  
  
 **参照**  
 使用すると、システムとネットワーク、データベースまたはデータ ソースに接続するディレクトリを検索できます。  
  
 **Options**  
 Visual FoxPro ODBC ドライバーのオプションを設定できるように、ダイアログ ボックスを展開します。  
  
## <a name="driver"></a>Driver  
 **照合順序**  
 フィールドが並べ替えられたシーケンスです。 既定の順序は、オペレーティング システムの言語バージョンでサポートされているシーケンスを反映します。 サポートされている照合順序の一覧は、次を参照してください。 [COLLATE 設定](../../odbc/microsoft/set-collate-command.md)です。  
  
 **[Exclusive]**  
 このチェック ボックスがオンの場合、ドライバーは、データ ソースを使用してデータにアクセスするときにのみ、Visual FoxPro データベースを開きます。 他のユーザーには、データベースが排他的に開かれたときに、データベースまたはデータベース内のテーブルをアクセスできません。 排他的に開かれているデータベース内のテーブルは、共有として開かれます。 開く、テーブルにのみ、使用、[排他設定](../../odbc/microsoft/set-exclusive-command.md)コマンド。 このチェック ボックスが無効になっているときに**データベースの種類**に設定されている**フリー テーブル ディレクトリ**です。  
  
 **Null**  
 ALTER TABLE と CREATE TABLE で作成される列が null 値を許容するかどうかを判断します。 場合は Null に設定すると、挿入 – SQL は – SQL insert ステートメントに含まれていない任意の列に null 値を挿入しています.VALUE 句。 Null が OFF の場合は空白が挿入されます。 次のコードのように渡された接続文字列で、このオプションを制御することもできます。  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **削除**  
 削除済みとしてマークされている行が返されるかどうかを決定します。 次のコードのように渡された接続文字列で、このオプションを制御することもできます。  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **バック グラウンドでのデータのフェッチ**  
 レコードが (プログレッシブ フェッチ)、バック グラウンドでフェッチされるか、アプリケーションが、結果セット内のすべてレコードがフェッチされるまでに待機するかどうかが決まります。
