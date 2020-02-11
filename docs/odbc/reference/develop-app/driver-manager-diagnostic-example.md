---
title: ドライバーマネージャーの診断の例 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 95392367b70af3eb820f0943af5dc668783a3fe5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046964"
---
# <a name="driver-manager-diagnostic-example"></a>ドライバー マネージャー診断の例
ドライバーマネージャーは診断メッセージを生成することもできます。 たとえば、アプリケーションで**Sqldatasources ソース**に無効な direction オプションが渡された場合、ドライバーマネージャーは**SQLGetDiagRec**から次の値を書式設定して返します。  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 このエラーは Driver Manager で発生したため、ベンダ ([Microsoft]) とその識別子 ([ODBC Driver Manager]) の診断メッセージにプレフィックスが追加されました。
