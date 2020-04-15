---
title: ドライバー マネージャーの診断例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 839095e5544cab73cdddd4f4b17a3d8d52136c9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305813"
---
# <a name="driver-manager-diagnostic-example"></a>ドライバー マネージャー診断の例
ドライバー マネージャーは、診断メッセージを生成することもできます。 たとえば、アプリケーションが無効な方向オプションを**SQLDataSources**に渡した場合、ドライバー マネージャーは **、SQLGetDiagRec**から次の値をフォーマットして返す可能性があります。  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 エラーは、ドライバー マネージャーで発生したため、ベンダー ([Microsoft]) とその識別子 ([ODBC ドライバー マネージャー]) の診断メッセージにプレフィックスを追加します。
