---
title: ODBC Core サブキー |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98c9380083eb5a0ad796f436af271564676b757d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094009"
---
# <a name="odbc-core-subkey"></a>ODBC Core サブキー
ODBC Core サブキーの下の値は、コアコンポーネント (ドライバーマネージャー、カーソルライブラリ、インストーラー DLL など) の使用回数を示します。 この値の形式を次の表に示します。  
  
|Name|データ型|データ|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 たとえば、3つの異なるアプリケーション用のセットアッププログラムによって ODBC Core コンポーネントがインストールされていて、2つの異なるドライバーがインストールされているとします。 ODBC Core サブキーの下の値は次のようになります。  
  
```  
UsageCount : REG_DWORD : 0x5  
```
