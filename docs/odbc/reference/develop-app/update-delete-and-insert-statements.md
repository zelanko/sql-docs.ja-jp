---
title: UPDATE、DELETE、および INSERT ステートメント |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2a2787be1bf44e1f214d396444a73b938acf7ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942838"
---
# <a name="update-delete-and-insert-statements"></a>UPDATE、DELETE、INSERT ステートメント
SQL ベースのアプリケーションは、 **UPDATE**、 **DELETE**、および**INSERT**の各ステートメントを実行して、テーブルに変更を加えます。 これらのステートメントは、SQL 文法の最小一致レベルに含まれており、すべてのドライバーとデータソースでサポートされている必要があります。  
  
 これらのステートメントの構文は次のとおりです。  
  
 **** _テーブル名の_更新  
  
 **** _列識別子_ **=** {*expression* &#124; **NULL**} の設定  
  
 [**,** _列識別子_ **=** {*式*&#124; **NULL**}]...  
  
 [**** _検索条件_]  
  
 _テーブル名_**からの削除**[**** _検索条件_]  
  
 **INSERT INTO** _table-name_[**(** _列識別子_[**,** _列識別子_]...**)**]  
  
 {*クエリ指定*&#124;**値 (** _挿入_値 [**,** _挿入値_]...**)**}  
  
 *クエリ指定*要素は、コアと拡張 sql 文法でのみ有効であり、*式*と*検索条件*の要素がコアと拡張 sql 文法でより複雑になることに注意してください。  
  
 他の SQL ステートメントと同様に、 **UPDATE**、 **DELETE**、および**INSERT**の各ステートメントは、多くの場合、パラメーターを使用する方が効率的です。 たとえば、Orders テーブルに複数の行を挿入するために、次のステートメントを準備して繰り返し実行することができます。  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 この効率性は、パラメーター値の配列を渡すことによって増やすことができます。 ステートメントパラメーターとパラメーター値の配列の詳細については、「[ステートメントパラメーター](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。
