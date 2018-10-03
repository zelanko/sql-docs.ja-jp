---
title: SQLSpecialColumns (Visual FoxPro ODBC ドライバー) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 7c4095448b8a9068dad3c4df1c28065e7cffbd67
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721149"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックでには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 サポート: 完全な  
  
 レベル 1 の ODBC API 準拠:  
  
 テーブルの行を一意に識別する最適な列のセットを取得します。  
  
 Visual FoxPro ODBC ドライバーでは、FoxPro テーブルに主キーを構成する列を返します。 (を参照してください[SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md))。呼び出した場合*fColType* SQL_ROWVER に設定すると、列は返されません。 **SQLSpecialColumns**にあるデータ ソースに対してのみ機能[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)します。  
  
 詳細については、次を参照してください。 [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)で、 *ODBC プログラマ リファレンス*します。
