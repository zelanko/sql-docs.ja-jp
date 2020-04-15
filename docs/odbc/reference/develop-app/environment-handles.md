---
title: 環境ハンドル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b504995e99dfad032598485e370b4d5a6681ae81
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300442"
---
# <a name="environment-handles"></a>環境ハンドル
*環境*は、データにアクセスするグローバルコンテキストです。環境に関連付けられている情報は、次のような本質的にグローバルな情報です。  
  
-   環境の状態  
  
-   現在の環境レベルの診断  
  
-   環境に現在割り当てられている接続のハンドル  
  
-   各環境属性の現在の設定  
  
 ODBC (ドライバー マネージャーまたはドライバー) を実装するコードの一部内で、環境ハンドルは、この情報を含む構造体を識別します。  
  
 環境ハンドルは、ODBC アプリケーションで頻繁には使用されません。 これらは常に**SQL データソース**および SQL**ドライバー**の呼び出しで使用され **、SQLAllocHandle** **、SQLEndTran** **、SQL フリーハンドル、SQLGetDiagField**、および**SQLGetDiagRec**の呼び出しで使用されることもあります。 **SQLGetDiagField**  
  
 ODBC (ドライバー マネージャーまたはドライバー) を実装するコードの各部分には、1 つまたは複数の環境ハンドルが含まれています。 たとえば、ドライバー マネージャーは、接続されているアプリケーションごとに個別の環境ハンドルを保持します。 環境ハンドルは**SQLAllocHandle**で割り当てられ **、SQLFreeHandle**で解放されます。
