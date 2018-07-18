---
title: SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed3bdb4cc5c2508435bff011545b5b9113d7aeac
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424391"
---
# <a name="sqlcancel"></a>SQLCancel
  [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)トピックでは、ことを示す odbc 2.x、アプリケーションを呼び出す場合`SQLCancel`場合、ステートメントの処理は行われません`SQLCancel`と同じ効果`SQLFreeStmt`で、`SQL_CLOSE`オプションですこの。完全を期すのためだけの動作が定義されているし、アプリケーションを呼び出す必要があります`SQLFreeStmt`または`SQLCloseCursor`カーソルを閉じます。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ クライアント アプリケーションで ODBC API バージョンを 3.5.x 以降に設定した場合も、`SQLCancel` 関数では、ODBC 2.x の動作が使用されます。  
  
## <a name="see-also"></a>参照  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
