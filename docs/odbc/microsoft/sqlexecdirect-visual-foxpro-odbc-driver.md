---
title: SQLExecDirect (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0086dc41e34ac543cf0cd560332454b0024de48e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 新しい実行[準備可能な SQL ステートメント](../../odbc/microsoft/visual-foxpro-terminology.md)です。 Visual FoxPro ODBC ドライバーは、ステートメントにパラメーターが存在しない場合、変数の現在値、パラメーター マーカーを使用します。  
  
 一度に 1 つ以上の SQL ステートメントを送信するのにバッチ コマンドを作成するには、バッチ内の各 SQL ステートメントを区切るため、セミコロン (;) を使用します。  
  
 テーブル、ビュー、またはフィールド名にスペースが含まれる場合を囲む名前背面に引用符記号。 たとえば、データベースには、テーブルとフィールド My Field という名前のテーブルが含まれている場合、囲みます識別子の各要素とおりを示します。  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 詳細については、次を参照してください。 [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md)で、 *ODBC プログラマ リファレンス*です。
