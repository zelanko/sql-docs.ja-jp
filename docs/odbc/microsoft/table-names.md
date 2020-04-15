---
title: テーブル名 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91a415cd456186f18ef358b9d504145f78152774
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303123"
---
# <a name="table-names"></a>テーブル名
dBASE、Microsoft Excel、パラドックス、またはテキスト ドライバを使用する場合、SELECT または DELETE の FROM 句、INSERT の INTO 句の後、および更新、テーブルの作成、および DROP TABLE の後に存在するテーブル名には、有効なパス、プライマリ名、およびファイル名拡張子を含めることができます。  
  
 SQL ステートメント内の他の場所で表名を使用しても、パスまたは拡張の使用はサポートされませんが、1 次名 (例えば、EMP FROM C:\ABC\EMP) のみを受け入れます。  
  
 相関名 (別名) を使用できます。 次に例を示します。  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
