---
title: DELETE - SQL コマンド |Microsoft ドキュメント
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
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea0b09d77b6d2df8ddd525df17526573b6a1e1be
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="delete---sql-command"></a>SQL コマンドを削除します。
削除対象のレコードをマークします。  
  
 Visual FoxPro ODBC ドライバーでは、このコマンドのネイティブの Visual FoxPro 言語の構文をサポートしています。 ドライバー固有の情報は、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>引数  
 [ *DatabaseName!*]*TableName*  
 レコードが削除対象としてマークするテーブルを指定します。  
  
 *DatabaseName!* 包含データベースは、データ ソースで指定されたデータベースではない場合は、テーブルを含むデータベースの名前を指定します。 データベースが、データ ソースで指定されたデータベースではない場合は、テーブルを含むデータベースの名前を含める必要があります。 データベース名の後に感嘆符 (!) 区切り記号は、テーブル名の前にあります。  
  
 ここで*FilterCondition1*[AND&#124;または*FilterCondition2*...]  
 Visual FoxPro が特定のレコードの削除だけをマークすることを指定します。  
  
 *FilterCondition*レコードが削除用のマークを満たす必要がある条件を指定します。 AND で接続すること、必要な数のフィルター条件を含めることができますか、OR 演算子。 NOT 演算子を使用して、論理式の値を反転するまたは使用することができます**空**フィールドが空の確認に関するページ ()。  
  
## <a name="remarks"></a>解説  
 削除設定が ON に設定した場合は、スコープが含まれているすべてのコマンドによってレコードが削除対象としてマークが無視されます。  
  
 -SQL ユース削除開いたテーブル内の削除用の複数のレコードをマークするときのレコード ロックの共有のアクセス。 これにより、マルチ ユーザー環境でのレコードの競合が軽減されるが、パフォーマンスが低下することができます。 最高のパフォーマンスを排他的に使用するテーブルを開きます。  
  
## <a name="driver-remarks"></a>ドライバーの解説  
 アプリケーションは、ODBC SQL ステートメントの削除をデータ ソースに送信するときに Visual FoxPro ODBC ドライバーは、Visual FoxPro DELETE コマンドは、変換せずに、コマンドに変換します。  
  
## <a name="see-also"></a>参照  
 [SET DELETED コマンド](../../odbc/microsoft/set-deleted-command.md)
