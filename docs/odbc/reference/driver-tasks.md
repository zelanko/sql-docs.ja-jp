---
title: ドライバーのタスク |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
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
ms.openlocfilehash: c7e351a84272e8ab9bd558e93e0d12bdc8275884
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
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
