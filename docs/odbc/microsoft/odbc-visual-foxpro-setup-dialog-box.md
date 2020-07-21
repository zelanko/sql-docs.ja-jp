---
title: '[ODBC Visual FoxPro セットアップ] ダイアログボックス |Microsoft Docs'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298082"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>ODBC Visual FoxPro セットアップ ダイアログ ボックス
[ **ODBC Visual Foxpro セットアップ**] ダイアログボックスを使用すると、visual foxpro データソースを追加または変更できます。  
  
 ドライバーをダウンロードするには、 [Visual FOXPRO ODBC ドライバーのダウンロードサイト](https://go.microsoft.com/fwlink/?LinkId=121318)を参照してください。  
  
## <a name="dialog-box-options"></a>ダイアログ ボックス オプション  
 **データソース名**  
 データソースに使用する名前を入力します。  
  
 **説明**  
 データソースの説明を入力します。  
  
 **データベースの種類**  
 データソースを接続するデータベースの種類を選択できます。  
  
 **Visual FoxPro データベース (。DBC**  
 データソースが Visual FoxPro[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)(dbc ファイル) と、データベース内のすべてのテーブルおよびローカルビューに接続することを指定します。  
  
 **フリーテーブルディレクトリ**  
 データソースが[フリーテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリに接続することを指定します。 [Sqlcolumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)や[SQLCOLUMNS](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)などの ODBC カタログ関数では、同じディレクトリ内のすべての[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)テーブルが無視されます。 データベーステーブルには、 [Sqlexecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md)と[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)を通じて送信される SQL SELECT ステートメントを使用してアクセスできます。  
  
 **パス**  
 データソースが接続するデータベースまたはフリーテーブルのディレクトリのパスと名前が表示されます。  
  
 **参照**  
 データソースを接続するデータベースまたはディレクトリのシステムとネットワークを検索できます。  
  
 **[オプション]**  
 ダイアログボックスを展開して、Visual FoxPro ODBC ドライバーのオプションを設定できるようにします。  
  
## <a name="driver"></a>ドライバー  
 **照合順序**  
 フィールドの並べ替え順序。 既定のシーケンスは、使用しているオペレーティングシステムの言語バージョンでサポートされているシーケンスを反映しています。 サポートされている照合シーケンスの一覧については、「 [COLLATE の設定](../../odbc/microsoft/set-collate-command.md)」を参照してください。  
  
 **[Exclusive]**  
 このチェックボックスをオンにすると、データソースを使用してデータにアクセスしたときに、ドライバーによって Visual FoxPro データベースのみが開かれます。 データベースが排他的に開かれている間、他のユーザーがデータベースまたはデータベース内のテーブルにアクセスすることはできません。 排他的に開かれているデータベース内のテーブルは、共有として開かれます。 テーブルを排他的に開くには、 [SET EXCLUSIVE](../../odbc/microsoft/set-exclusive-command.md)コマンドを使用します。 このチェックボックスは、[**データベースの種類**] が [**フリーテーブルディレクトリ**] に設定されている場合は無効になります。  
  
 **[Null]**  
 ALTER TABLE と CREATE TABLE で作成された列が null 値を許容するかどうかを決定します。 Null をに設定すると、INSERT-SQL によって挿入されていない任意の列に null 値が挿入されます。VALUE 句。 Null が OFF の場合は、空白が挿入されます。 このオプションは、次のコードのように、渡された接続文字列を使用して制御することもできます。  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Deleted**  
 削除済みとしてマークされた行が返されるかどうかを判断します。 このオプションは、次のコードのように、渡された接続文字列を使用して制御することもできます。  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **バックグラウンドでデータをフェッチする**  
 レコードがバックグラウンドでフェッチされるか (プログレッシブフェッチ)、結果セット内のすべてのレコードがフェッチされるまでアプリケーションが待機するかを決定します。
