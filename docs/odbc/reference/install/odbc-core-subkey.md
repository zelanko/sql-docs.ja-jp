---
title: ODBC Core サブキー |Microsoft ドキュメント
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
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf8e143a8d5d329fe3eb68185a3ebdf8f7f6cd6b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-core-subkey"></a>ODBC Core サブキー
ODBC Core サブキーの下にある値は、コア コンポーネント (ドライバー マネージャー、カーソル ライブラリ、インストーラー DLL、およびなど) の使用率カウントを示します。 この値の形式は次の表に示します。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 たとえば、ODBC コア コンポーネントは、3 種類のアプリケーションと 2 つの異なるドライバーのセットアップ プログラムによってインストールされているとします。 ODBC Core サブキーの下の値は次のようになります。  
  
```  
UsageCount : REG_DWORD : 0x5  
```
