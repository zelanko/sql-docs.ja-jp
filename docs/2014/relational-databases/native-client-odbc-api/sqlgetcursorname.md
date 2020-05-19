---
title: Sqlgetカーソル名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7e9161170665d421b235a3a121ab8bb761e32daf
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706064"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
  アプリケーションでカーソル名が指定されていない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーによって、カーソルの生成時にアプリケーション用に1つが生成されます。 アプリケーションでは、 **Sqlgetcursor name**を使用して、位置指定の UPDATE および DELETE ステートメントのドライバーで定義されたカーソル名を取得できます。 アプリケーションでは、位置指定データ操作ステートメントを利用するために**SQLSetCursorName**を呼び出す必要はありません。  
  
## <a name="see-also"></a>参照  
 [Sqlgetカーソル名関数](https://go.microsoft.com/fwlink/?LinkId=59349)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
