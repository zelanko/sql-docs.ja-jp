---
title: "SQLSpecialColumns (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3128dca9f473008b5e5fcae234fd9ba119911e81
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 テーブル内の行を一意に識別する列の最適なセットを取得します。  
  
 Visual FoxPro ODBC ドライバーでは、FoxPro テーブルに主キーを構成する列を返します。 (を参照してください[SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md))。呼び出した場合*fColType* SQL_ROWVER に設定すると、列は返されません。 **SQLSpecialColumns**にあるデータ ソースに対してのみ機能[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)です。  
  
 詳細については、次を参照してください。 [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)で、 *ODBC プログラマ リファレンス*です。

