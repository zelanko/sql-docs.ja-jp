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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b5a7e09a6dd9bbcc50ddbaf70b911260e96cde4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214682"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
  手動コミット モードで呼び出して**SQLFreeHandle**ステートメントでは、開いているトランザクションがあるハンドルによりの保留中のデータベースに変更のロールバックされます。 呼び出す**SQLFreeHandle**ステートメントでハンドル常に開いているカーソルを閉じて破棄保留中の結果、ステートメント ハンドルに関連付けられたすべてのリソースを解放します。  
  
## <a name="see-also"></a>参照  
 [SQLFreeHandle 関数](http://go.microsoft.com/fwlink/?LinkId=59345)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
