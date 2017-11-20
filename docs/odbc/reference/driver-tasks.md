---
title: "ドライバーのタスク |Microsoft ドキュメント"
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 331e3aee3a4a60cbfa1a1308b71da80bf9772f23
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="driver-tasks"></a>ドライバーのタスク
ドライバーで実行される特定のタスクは次のとおりです。  
  
-   接続して、データ ソースからの接続を切断します。  
  
-   未チェック ドライバー マネージャーによって関数のエラーを確認しています。  
  
-   トランザクションを開始していますこれは、アプリケーションに対して透過的です。  
  
-   実行のためのデータ ソースへの SQL ステートメントを送信しています。 ドライバーは、DBMS に固有の sql; ODBC SQL を変更する必要があります。多くの場合、これは、DBMS に固有の SQL を使用した ODBC で定義されたエスケープ句を置き換えるに制限されます。  
  
-   データを送信し、アプリケーションで指定されたデータ型を変換する場合など、データ ソースからのデータの取得。  
  
-   ODBC SQLSTATEs DBMS 固有のエラーにマップします。

