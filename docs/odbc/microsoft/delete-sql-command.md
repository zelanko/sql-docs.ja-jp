---
title: DELETE-SQL コマンド |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303553"
---
# <a name="delete---sql-command"></a>DELETE - SQL コマンド
削除対象のレコードをマークします。  
  
 Visual FoxPro ODBC ドライバーでは、このコマンドのネイティブな Visual FoxPro 言語構文がサポートされています。 ドライバー固有の情報については、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>引数  
 [ *DatabaseName!*] から*TableName*  
 レコードを削除対象としてマークするテーブルを指定します。  
  
 *DatabaseName!* 包含データベースがデータソースで指定されたデータベースでない場合に、テーブルを含むデータベースの名前を指定します。 データベースがデータソースで指定されたデータベースでない場合は、テーブルを含むデータベースの名前を含める必要があります。 データベース名の後とテーブル名の前に、感嘆符 (!) の区切り記号を含めます。  
  
 WHERE *FilterCondition1*[および &#124; または*FilterCondition2*...]  
 Visual FoxPro が特定のレコードのみを削除するようにマークすることを指定します。  
  
 *Filtercondition*は、削除対象としてマークするためにレコードが満たす必要のある条件を指定します。 フィルター条件はいくつでも含めることができ、AND または OR 演算子を使用して接続できます。 また、NOT 演算子を使用して論理式の値を反転させることも、 **empty**() を使用して空のフィールドをチェックすることもできます。  
  
## <a name="remarks"></a>Remarks  
 [削除の設定] が ON に設定されている場合、削除用にマークされたレコードは、スコープを含むすべてのコマンドで無視されます。  
  
 DELETE-SQL は、共有アクセス用に開かれたテーブルで複数のレコードの削除をマークするときに、レコードロックを使用します。 これにより、マルチユーザー環境でのレコードの競合が減少しますが、パフォーマンスが低下する可能性があります。 パフォーマンスを最大にするには、テーブルを排他的に使用するために開きます。  
  
## <a name="driver-remarks"></a>ドライバーの解説  
 アプリケーションが ODBC SQL ステートメントの削除をデータソースに送信すると、Visual FoxPro ODBC ドライバーはコマンドを変換せずに Visual FoxPro DELETE コマンドに変換します。  
  
## <a name="see-also"></a>参照  
 [SET DELETED コマンド](../../odbc/microsoft/set-deleted-command.md)
