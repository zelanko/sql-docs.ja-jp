---
title: "DROP TABLE コマンド |Microsoft ドキュメント"
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
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f346bc3701df00cdddf5e6af77f500017570bd51
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="drop-table-command"></a>DROP TABLE コマンド
データ ソースに指定されたデータベースからテーブルを削除し、ディスクから削除します。  
  
 Visual FoxPro ODBC ドライバーでは、このコマンドのネイティブの Visual FoxPro 言語の構文をサポートしています。 ドライバー固有の情報は、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>[設定]  
 *テーブル名*  
 データ ソースに指定されたデータベースから削除して、ディスクから削除するテーブルを指定します。  
  
 *FileName*  
 空きディスクから削除するテーブルを指定します。  
  
 ?  
 データ ソースに指定されたデータベースから削除して、ディスクから削除するテーブルを選択できる [削除] ダイアログを表示します。  
  
## <a name="remarks"></a>解説  
 DROP TABLE が発行されると、すべてのプライマリ インデックス、既定値、およびテーブルに関連付けられている検証規則も削除されます。 DROP TABLE は、それらのテーブルにルールがある場合に、データ ソースで指定されたデータベースまたはリレーションが削除されているテーブルに関連付けられているその他のテーブルにも影響します。 ルールとの関係は無効になります、テーブルがデータベースから削除されたときにします。  
  
## <a name="driver-remarks"></a>ドライバーの解説  
 アプリケーションは、DROP TABLE の ODBC SQL ステートメントをデータ ソースに送信するときに Visual FoxPro ODBC ドライバーは、次の表に示す構文を使用して、ビジュアルの FoxProDROP テーブル コマンドにコマンドを変換します。  
  
|ODBC 構文|データ ソース|Visual FoxPro 構文|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE*ベース テーブル名*|データベース (.dbc ファイル)|削除するテーブル*TableName*削除|  
||空きテーブル (.dbf ファイル) のディレクトリ|消去*dbfName*<br /><br /> 消去*cdxName*<br /><br /> 消去*fptName*|

