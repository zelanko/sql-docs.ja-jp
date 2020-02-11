---
title: Sql特殊列 (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b690cceecb6c9980f5d84e96bccb1b02f014c026
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093096"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: レベル1  
  
 テーブル内の行を一意に識別する最適な列のセットを取得します。  
  
 Visual FoxPro ODBC ドライバーは、FoxPro テーブルの主キーを構成する列を返します。 (「 [Sqlprimarykeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md)」を参照してください)。*Fcoltype*を SQL_ROWVER に設定して呼び出された場合、列は返されません。 **Sql特殊列**は、[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)であるデータソースに対してのみ機能します。  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [sqlの列](../../odbc/reference/syntax/sqlspecialcolumns-function.md)」を参照してください。
