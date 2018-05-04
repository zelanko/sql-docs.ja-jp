---
title: ODBC 関数が、カーソル ライブラリでは実行されません |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: f2941522-75eb-4db9-9468-4800b884dac2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e55b1351f31ccee3ea5ef08396938835f04985c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-functions-not-executed-by-the-cursor-library"></a>ODBC 関数が、カーソル ライブラリでは実行されません。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリでは、次の関数は実行されません。 アプリケーションでは、これらの関数のいずれかを呼び出して、ドライバー マネージャーは、ドライバーでは、カーソル ライブラリではなくを呼び出します。  
  
|||  
|-|-|  
|**SQLFetch**|**SQLGetEnvAttr**|  
|**SQLGetConnectAttr**|**Sqlsetdescrec による**|  
|**SQLGetDiagField**|**SQLSetEnvAttr**|  
|**SQLGetDiagRec**||
