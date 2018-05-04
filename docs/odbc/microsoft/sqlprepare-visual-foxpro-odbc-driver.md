---
title: SQLPrepare (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42eabe40eb5324cf82c543525ce286dadc2a510a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
