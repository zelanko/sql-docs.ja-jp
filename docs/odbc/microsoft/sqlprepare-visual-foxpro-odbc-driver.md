---
title: "SQLPrepare (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b810cd3adff4e5903a3ce515eb501b4a8f202c14
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 最適化し、ステートメントを実行する方法を計画することで、SQL ステートメントを準備します。 実行するため、SQL ステートメントがコンパイルされた[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)です。  
  
 テーブル、ビュー、またはフィールド名にスペースが含まれる場合、名囲みます背面に引用符 (') のマーク。 たとえば、データベースには、テーブルとフィールド My Field という名前のテーブルが含まれている場合、囲みます識別子の各要素とおりを示します。  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 詳細については、次を参照してください。 [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)で、 *ODBC プログラマ リファレンス*です。
