---
title: "行の状態 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60931ff8464478a55828713747ad6f4bb408f10d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="row-status"></a>行の状態
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリでは、行の状態のキャッシュにバッファーを作成します。 カーソル ライブラリは、このバッファーから (SQL_ATTR_ROW_STATUS_PTR ステートメント属性を持つ指定された) 行の状態配列の値を取得します。 行ごとに、カーソル ライブラリこのバッファーを設定します。  
  
-   SQL_ROW_DELETED、位置指定が実行されるとは、行のステートメントを削除します。  
  
-   使用して、データ ソースから行を取得中にエラーが発生して SQL_ROW_ERROR **SQLFetch**です。  
  
-   正常に使用して、データ ソースから行をフェッチと SQL_ROW_SUCCESS **SQLFetch**です。  
  
-   SQL_ROW_UPDATED 行に位置指定の update ステートメントを実行するとします。
