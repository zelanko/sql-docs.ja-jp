---
title: ODBC コア サブキー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9e6bfcf3c1efa87076e6d3e27a438cde6f794157
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304058"
---
# <a name="odbc-core-subkey"></a>ODBC Core サブキー
ODBC Core サブキーの下の値は、コア コンポーネント (ドライバー マネージャー、カーソル ライブラリ、インストーラー DLL など) の使用量カウントを示します。 この値の形式を次の表に示します。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|使用カウント|REG_DWORD|*count*|  
  
 たとえば、ODBC Core コンポーネントが、3 つの異なるアプリケーションと 2 つの異なるドライバのセットアップ プログラムによってインストールされているとします。 ODBC コア サブキーの下の値は次のようになります。  
  
```  
UsageCount : REG_DWORD : 0x5  
```
