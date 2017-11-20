---
title: "環境ハンドル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f563e798c985ebb8ea8ab7925ed39f3d154d144
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="environment-handles"></a>環境ハンドル
*環境*はデータにアクセスするためのグローバル コンテキストは、環境に関連付けられているなど、本質的にグローバルに適用される情報。  
  
-   環境の状態  
  
-   現在の環境レベルの診断  
  
-   環境に現在割り当てられている接続の処理  
  
-   環境の各属性の現在の設定  
  
 ODBC ドライバー マネージャー (ドライバー) を実装するコードの部分、内では、環境ハンドルは、この情報を格納する構造体を識別します。  
  
 環境ハンドルは、ODBC アプリケーションで頻繁には使用されません。 呼び出しで常に使用される**SQLDataSources**と**SQLDrivers**への呼び出しでときどき使わと**SQLAllocHandle**、 **SQLEndTran**、**SQLFreeHandle**、 **SQLGetDiagField**、および**SQLGetDiagRec**です。  
  
 ODBC ドライバー マネージャー (ドライバー) を実装するコードの各部分には、1 つまたは複数の環境ハンドルが含まれています。 たとえば、ドライバー マネージャーは、それに接続されている各アプリケーションの別の環境ハンドルを保持します。 環境ハンドルが割り当てられます**SQLAllocHandle**およびに解放された**SQLFreeHandle**です。

