---
title: "行の状態 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8f164b8269e1150cdf7a85e486bcc3fd93a9411f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="row-status"></a>行の状態
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリでは、行の状態のキャッシュにバッファーを作成します。 カーソル ライブラリは、このバッファーから (SQL_ATTR_ROW_STATUS_PTR ステートメント属性を持つ指定された) 行の状態配列の値を取得します。 行ごとに、カーソル ライブラリこのバッファーを設定します。  
  
-   SQL_ROW_DELETED、位置指定が実行されるとは、行のステートメントを削除します。  
  
-   使用して、データ ソースから行を取得中にエラーが発生して SQL_ROW_ERROR **SQLFetch**です。  
  
-   正常に使用して、データ ソースから行をフェッチと SQL_ROW_SUCCESS **SQLFetch**です。  
  
-   SQL_ROW_UPDATED 行に位置指定の update ステートメントを実行するとします。

