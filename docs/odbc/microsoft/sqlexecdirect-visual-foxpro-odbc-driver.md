---
title: SQLExecDirect (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ed4f8501146221737a5af6c33d2196cb92704157
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
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
