---
title: "ODBC Core サブキー |Microsoft ドキュメント"
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
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9331aa39d5df84cc5269fb995c594df9cd08e27f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-core-subkey"></a>ODBC Core サブキー
ODBC Core サブキーの下にある値は、コア コンポーネント (ドライバー マネージャー、カーソル ライブラリ、インストーラー DLL、およびなど) の使用率カウントを示します。 この値の形式は次の表に示します。  
  
|[オブジェクト名]|データ型|data|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 たとえば、ODBC コア コンポーネントは、3 種類のアプリケーションと 2 つの異なるドライバーのセットアップ プログラムによってインストールされているとします。 ODBC Core サブキーの下の値は次のようになります。  
  
```  
UsageCount : REG_DWORD : 0x5  
```
