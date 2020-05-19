---
title: SQLFreeHandle |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9345a02d446d8a4b7b82e9652444a08f68641f87
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706077"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
  手動コミットモードでは、トランザクションが開いているステートメントハンドルで**Sqlfreehandle**を呼び出すと、データベースに対する保留中の変更がロールバックされます。 ステートメントハンドルで**Sqlfreehandle**を呼び出すと、開いているカーソルが常に閉じられ、保留中の結果は破棄され、ステートメントハンドルに関連付けられているすべてのリソースが解放されます。  
  
## <a name="see-also"></a>参照  
 [SQLFreeHandle 関数](https://go.microsoft.com/fwlink/?LinkId=59345)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
