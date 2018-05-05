---
title: ドライバーのタスク |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b8ea61df89eb6f4e21a57e71a4277d56b16add5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="driver-tasks"></a>ドライバーのタスク
ドライバーで実行される特定のタスクは次のとおりです。  
  
-   接続して、データ ソースからの接続を切断します。  
  
-   未チェック ドライバー マネージャーによって関数のエラーを確認しています。  
  
-   トランザクションを開始していますこれは、アプリケーションに対して透過的です。  
  
-   実行のためのデータ ソースへの SQL ステートメントを送信しています。 ドライバーは、DBMS に固有の sql; ODBC SQL を変更する必要があります。多くの場合、これは、DBMS に固有の SQL を使用した ODBC で定義されたエスケープ句を置き換えるに制限されます。  
  
-   データを送信し、アプリケーションで指定されたデータ型を変換する場合など、データ ソースからのデータの取得。  
  
-   ODBC SQLSTATEs DBMS 固有のエラーにマップします。
