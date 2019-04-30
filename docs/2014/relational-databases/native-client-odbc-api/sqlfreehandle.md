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
ms.openlocfilehash: 197d3e1d36f8513821cec9630cade8f52681a43d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63154664"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
  手動コミット モードで呼び出して**SQLFreeHandle**ステートメントでは、開いているトランザクションがあるハンドルによりの保留中のデータベースに変更のロールバックされます。 呼び出す**SQLFreeHandle**ステートメントでハンドル常に開いているカーソルを閉じて破棄保留中の結果、ステートメント ハンドルに関連付けられたすべてのリソースを解放します。  
  
## <a name="see-also"></a>参照  
 [SQLFreeHandle 関数](https://go.microsoft.com/fwlink/?LinkId=59345)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
