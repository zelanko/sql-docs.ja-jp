---
title: SQL コマンドの更新プログラム - |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 748a405ba63fb934eee162d3cc023b5935251cea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908677"
---
# <a name="update---sql-command"></a>更新プログラム - SQL コマンドします。
新しい値では、テーブル内のレコードを更新します。  
  
 Visual FoxPro ODBC ドライバーでは、このコマンドのネイティブの Visual FoxPro 言語の構文をサポートしています。 ドライバー固有の情報を参照してください。**ドライバー解説**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>引数  
 更新 [ *DatabaseName1!*]*TableName1*  
 レコードが新しい値で更新されるテーブルを指定します。  
  
 *DatabaseName1!* テーブルを含むデータ ソースで指定されたデータベース以外のデータベースの名前を指定します。 データベースが現在のものではない場合は、テーブルを含むデータベースの名前を含める必要があります。 データベース名の後に感嘆符 (!) 区切り記号は、テーブル名の前にあります。  
  
 設定*Column_Name1*= *eExpression1*[、 *Column_Name2*= *eExpression2*  
 更新される列とその新しい値を指定します。 WHERE 句を省略した場合は、同じ値を持つ列のすべての行が更新されます。  
  
 ここで*FilterCondition1*[AND&#124;または*FilterCondition2*...]  
 新しい値で更新するレコードを指定します。  
  
 *FilterCondition*を新しい値で更新するレコードが満たす必要がある条件を指定します。 必要な場合、それらを AND で接続数のフィルター条件を含めることができますか、OR 演算子。 NOT 演算子を使用して、論理式の値を反転するまたは使用することができます**空**フィールドが空の確認に関するページ ()。  
  
## <a name="remarks"></a>解説  
 更新プログラム - SQL は、1 つのテーブルのレコードだけを更新できます。  
  
 置換 とは異なりは、更新 - SQL は、レコードのロックがテーブル内の複数のレコードを更新する共有アクセスで開かれたときに使用されます。 これにより、マルチ ユーザー環境でのレコードの競合が軽減されるが、パフォーマンスが低下することができます。 パフォーマンスを高めるため、テーブルを開きます排他的な使用か使用**FLOCK**に関するページ ()、テーブルをロックします。  
  
## <a name="driver-remarks"></a>ドライバーの解説  
 アプリケーションは、ODBC SQL ステートメントの更新をデータ ソースに送信するときに Visual FoxPro ODBC ドライバーを翻訳しないで Visual FoxProUPDATE コマンドに、コマンドに変換します。  
  
## <a name="see-also"></a>参照  
 [SQL コマンドを削除します。](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT - SQL コマンド](../../odbc/microsoft/insert-sql-command.md)
