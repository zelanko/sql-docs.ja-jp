---
title: 削除 - SQL コマンド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9757fd57d999815964266c035963de1129eaf5e8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303553"
---
# <a name="delete---sql-command"></a>DELETE - SQL コマンド
レコードを削除対象としてマークします。  
  
 ビジュアル フォックスプロ ODBC ドライバーは、このコマンドのネイティブの Visual FoxPro 言語構文をサポートしています。 ドライバ固有の情報については、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>引数  
 から [*データベース名!**テーブル名*  
 レコードが削除対象としてマークされるテーブルを指定します。  
  
 *Databasename！* 含まれているデータベースがデータ ソースで指定されたデータベースでない場合は、テーブルを含むデータベースの名前を指定します。 データベースがデータ ソースで指定されたデータベースでない場合は、テーブルを含むデータベースの名前を含める必要があります。 データベース名の後、テーブル名の前に感嘆符 (!) 区切り記号を含めます。  
  
 どこで*フィルター条件1*[&#124;または*フィルター条件2.]*  
 特定のレコードのみを削除対象としてマークすることを指定します。  
  
 *FilterCondition は*、レコードが削除対象としてマークするために満たす必要がある条件を指定します。 フィルター条件は、AND または OR 演算子で接続して、必要な数だけ組み込むことができます。 また、NOT 演算子を使用して論理式の値を逆にしたり **、EMPTY**( ) を使用して空のフィールドをチェックすることもできます。  
  
## <a name="remarks"></a>解説  
 SET DELETED が ON に設定されている場合、削除対象としてマークされたレコードは、スコープを含むすべてのコマンドによって無視されます。  
  
 DELETE - SQL は、共有アクセス用にオープンされたテーブルで複数のレコードに削除のマークを付けるとき、レコードロックを使用します。 これにより、マルチユーザーの状況でのレコード競合が減少しますが、パフォーマンスが低下する可能性があります。 パフォーマンスを最大限に高めるには、排他的に使用するためにテーブルを開きます。  
  
## <a name="driver-remarks"></a>ドライバの解説  
 アプリケーションが ODBC SQL ステートメント DELETE をデータ ソースに送信すると、変換なしでコマンドが Visual FoxPro DELETE コマンドに変換されます。  
  
## <a name="see-also"></a>参照  
 [SET DELETED コマンド](../../odbc/microsoft/set-deleted-command.md)
