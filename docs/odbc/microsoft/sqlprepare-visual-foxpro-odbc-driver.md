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
ms.openlocfilehash: 5835ddaf27d097dcfff608649f50c1f7f41a93df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67996307"
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: コアレベル  
  
 ステートメントを最適化および実行する方法を計画して、SQL ステートメントを準備します。 SQL ステートメントは、 [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)によって実行されるようにコンパイルされます。  
  
 テーブル、ビュー、またはフィールドの名前にスペースが含まれている場合は、名前を [戻る引用符] (') マークで囲みます。 たとえば、データベースに My Table という名前のテーブルとフィールド My Field が含まれている場合は、識別子の各要素を次のように囲みます。  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md) 」を参照してください。
