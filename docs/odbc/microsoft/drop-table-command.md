---
title: テーブルのドロップ コマンド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 779c519f720027aea3a6f6cf2587d3c6e0b59b52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303423"
---
# <a name="drop-table-command"></a>DROP TABLE コマンド
データ ソースで指定されたデータベースからテーブルを削除し、ディスクから削除します。  
  
 ビジュアル フォックスプロ ODBC ドライバーは、このコマンドのネイティブの Visual FoxPro 言語構文をサポートしています。 ドライバ固有の情報については、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>設定  
 *TableName*  
 データ ソースで指定されたデータベースから削除し、ディスクから削除するテーブルを指定します。  
  
 *FileName*  
 ディスクから削除する空きテーブルを指定します。  
  
 ?  
 [削除] ダイアログボックスを表示し、データ ソースで指定したデータベースから削除するテーブルを選択し、ディスクから削除できます。  
  
## <a name="remarks"></a>解説  
 DROP TABLE が発行されると、そのテーブルに関連付けられているすべてのプライマリ インデックス、デフォルト値、および検証規則も削除されます。 DROP TABLE は、削除するテーブルに関連付けられたルールまたはリレーションシップがテーブルに関連付けられている場合、データ ソースで指定されたデータベース内の他のテーブルにも影響します。 テーブルがデータベースから削除されると、ルールとリレーションは無効になります。  
  
## <a name="driver-remarks"></a>ドライバの解説  
 アプリケーションが ODBC SQL ステートメント DROP TABLE をデータ ソースに送信すると、次の表に示す構文を使用して、Visual FoxPro ODBC ドライバーはコマンドを Visual FoxProDROP TABLE コマンドに変換します。  
  
|ODBC 構文|データ ソース|ビジュアル フォックスプロの構文|  
|-----------------|-----------------|--------------------------|  
|ドロップ テーブル*ベース テーブル名*|データベース (.dbc ファイル)|テーブル*テーブル名の*削除|  
||空きテーブルのディレクトリ (.dbf ファイル)|*イレースド・データベース名*<br /><br /> *消去 cdx 名*<br /><br /> *消去 fptName*|
