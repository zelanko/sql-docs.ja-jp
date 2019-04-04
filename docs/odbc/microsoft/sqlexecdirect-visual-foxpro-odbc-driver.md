---
title: SQLExecDirect (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 808d7890c18839c0e9059cdc3181a4579eb2ec4f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716040"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックでには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 サポート: 完全な  
  
 ODBC API 準拠: コア レベル  
  
 新しい実行[準備可能な SQL ステートメント](../../odbc/microsoft/visual-foxpro-terminology.md)します。 Visual FoxPro ODBC ドライバーでは、任意のパラメーターは、ステートメントに存在しない場合、パラメーター マーカーの変数の現在の値が使用されます。  
  
 一度に 1 つ以上の SQL ステートメントを送信するバッチ コマンドを作成するには、セミコロン (;) を使用して、バッチ内の各 SQL ステートメントを区切ります。  
  
 テーブル、ビュー、またはフィールド名にスペースが含まれる場合の名前で囲みます引用符の背面にマークします。 たとえば、データベースにマイ テーブルとフィールド My Field という名前のテーブルが含まれている場合を囲む識別子の各要素として次のように。  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 詳細については、[SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md)で、 *ODBC プログラマ リファレンス*を参照してください。
