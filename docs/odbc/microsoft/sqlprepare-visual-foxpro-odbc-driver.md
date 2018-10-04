---
title: SQLPrepare (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3ef083829b1ce322f2cede53f853c80683f01cb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692180"
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックでには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 サポート: 完全な  
  
 ODBC API 準拠: コア レベル  
  
 最適化し、ステートメントを実行する方法を計画することにより、SQL ステートメントを準備します。 実行するため、SQL ステートメントがコンパイルされる[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)します。  
  
 テーブル、ビュー、またはフィールド名にスペースが含まれる場合の名前で囲みます背面に引用符 (') のマーク。 たとえば、データベースにマイ テーブルとフィールド My Field という名前のテーブルが含まれている場合を囲む識別子の各要素として次のように。  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 詳細については、次を参照してください。 [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)で、 *ODBC プログラマ リファレンス*します。
