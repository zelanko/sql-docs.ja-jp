---
title: 更新 - SQL コマンド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 818811c18ed52cef5bdb1c4d97f947bb86e67422
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307643"
---
# <a name="update---sql-command"></a>UPDATE - SQL コマンド
テーブル内のレコードを新しい値で更新します。  
  
 ビジュアル フォックスプロ ODBC ドライバーは、このコマンドのネイティブの Visual FoxPro 言語構文をサポートしています。 ドライバ固有の情報については、「**ドライバ解説**」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>引数  
 更新 [*データベース名1!**テーブル名1*  
 レコードが新しい値で更新されるテーブルを指定します。  
  
 *データベース名1!* テーブルを含むデータ ソースで指定されたデータベース以外のデータベースの名前を指定します。 データベースが現在のデータベースでない場合は、テーブルを含むデータベースの名前を含める必要があります。 データベース名の後、テーブル名の前に感嘆符 (!) 区切り記号を含めます。  
  
 *e 式1* *Column_Name1*= 設定 [, *Column_Name2*= *e 式2*  
 更新される列とその新しい値を指定します。 WHERE 句を省略すると、列内のすべての行が同じ値で更新されます。  
  
 どこで*フィルター条件1*[&#124;または*フィルター条件2.]*  
 新しい値で更新されるレコードを指定します。  
  
 *FilterCondition は*、レコードが新しい値で更新するために満たす必要がある条件を指定します。 フィルタ条件は、AND または OR 演算子で接続して、必要な数だけ含めることができます。 また、NOT 演算子を使用して論理式の値を逆にしたり **、EMPTY**( ) を使用して空のフィールドをチェックすることもできます。  
  
## <a name="remarks"></a>解説  
 更新 - SQL は、単一のテーブル内のレコードのみを更新できます。  
  
 REPLACE とは異なり、UPDATE - SQL は、共有アクセス用にオープンされた表の複数のレコードを更新するときにレコードロックを使用します。 これにより、マルチユーザーの状況でのレコード競合を減らすことができますが、パフォーマンスが低下する可能性があります。 パフォーマンスを最大にするには、排他的に使用するためにテーブルを開くか **、FLOCK**( ) を使用してテーブルをロックします。  
  
## <a name="driver-remarks"></a>ドライバの解説  
 アプリケーションが ODBC SQL ステートメント UPDATE をデータ ソースに送信すると、変換なしでコマンドが Visual FoxProUPDATE コマンドに変換されます。  
  
## <a name="see-also"></a>参照  
 [削除 - SQL コマンド](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT - SQL コマンド](../../odbc/microsoft/insert-sql-command.md)
