---
title: "ODBC Core サブキー |Microsoft ドキュメント"
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
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad7a45f0f3272e1e2d7ae799ab1ca86bfb90b9be
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-core-subkey"></a>ODBC Core サブキー
ODBC Core サブキーの下にある値は、コア コンポーネント (ドライバー マネージャー、カーソル ライブラリ、インストーラー DLL、およびなど) の使用率カウントを示します。 この値の形式は次の表に示します。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 たとえば、ODBC コア コンポーネントは、3 種類のアプリケーションと 2 つの異なるドライバーのセットアップ プログラムによってインストールされているとします。 ODBC Core サブキーの下の値は次のようになります。  
  
```  
UsageCount : REG_DWORD : 0x5  
```

