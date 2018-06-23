---
title: SQLCancel |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6aff7aea0040e2fd7f86a3ad668b4e4438148497
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177089"
---
# <a name="sqlcancel"></a>SQLCancel
  [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) ODBC でトピックを表示する 2.x、アプリケーションを呼び出す場合`SQLCancel`、ステートメントの処理が行われない場合に`SQLCancel`と同じ効果を持つ`SQLFreeStmt`で、`SQL_CLOSE`オプション; この完全を期すのためだけの動作が定義されているし、アプリケーションを呼び出す必要があります`SQLFreeStmt`または`SQLCloseCursor`カーソルを閉じます。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ クライアント アプリケーションで ODBC API バージョンを 3.5.x 以降に設定した場合も、`SQLCancel` 関数では、ODBC 2.x の動作が使用されます。  
  
## <a name="see-also"></a>参照  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  