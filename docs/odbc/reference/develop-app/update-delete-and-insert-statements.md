---
title: 更新、削除、および挿入ステートメント |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f12682a5d012d6981afce0085e9c920ed2f2ffbc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284262"
---
# <a name="update-delete-and-insert-statements"></a>UPDATE、DELETE、INSERT ステートメント
SQL ベースのアプリケーションは **、UPDATE** **、DELETE、****および INSERT**ステートメントを実行してテーブルを変更します。 これらのステートメントは、SQL の最小文法準拠レベルの一部であり、すべてのドライバーとデータ ソースでサポートされている必要があります。  
  
 これらのステートメントの構文は次のとおりです。  
  
 **テーブル**_名を_更新  
  
 **SET** _列識別子_**=**{*式*&#124; **NULL**}  
  
 [**,**_列識別子_**=**{*式*&#124; **NULL**} .  
  
 [**WHERE** _検索条件_]  
  
 _テーブル名_**から削除**[**WHERE** _検索条件_]  
  
 **テーブル**_名_[**(** _列識別子_[**,** _列識別子_] .**)**]  
  
 {*クエリ指定*&#124; **VALUES (** _挿入値_[**,** _挿入値_]..**)**}  
  
 *クエリ仕様*要素は、コアおよび拡張 SQL 文法でのみ有効であり、*式*と*検索条件*の要素は、コアおよび拡張 SQL 文法でより複雑になることに注意してください。  
  
 他の SQL ステートメントと同様に **、UPDATE** **、DELETE、** および**INSERT**ステートメントは、パラメーターを使用する場合に、より効率的な場合がよくあります。 たとえば、次のステートメントを準備し、繰り返し実行して Orders テーブルに複数の行を挿入できます。  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 この効率は、パラメータ値の配列を渡すことで向上させることができます。 ステートメント パラメータおよびパラメータ値の配列の詳細については、「ステートメント[パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。
