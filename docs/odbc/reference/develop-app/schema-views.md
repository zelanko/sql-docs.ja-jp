---
title: "スキーマ ビュー |Microsoft ドキュメント"
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
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d85a59f54fab5508c5781bfb29a1243c12b44e6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="schema-views"></a>スキーマ ビュー
ODBC カタログ関数を呼び出すことによって、または INFORMATION_SCHEMA ビューを使用して、アプリケーションは、DBMS からメタデータ情報を取得できます。 ビューは、ANSI sql-92 標準で定義されます。  
  
 DBMS およびドライバーによってサポートされる、INFORMATION_SCHEMA ビューは、ODBC カタログ関数のメタデータを取得するより強力で包括的な手段を提供します。 アプリケーションが独自のカスタムを実行できる**選択**に対してこれらのビューのいずれかのステートメントは、ビューに参加できますまたはビューに対して和集合を実行することができます。 大きいユーティリティとさまざまなメタデータを提供しながら INFORMATION_SCHEMA ビューは、DBMS によって多くの場合、サポートされていません。 これは、Dbms とドライバーの詳細、sql-92 と順守の実現とに変更する可能性があります。  
  
 アプリケーションが呼び出す調べるにはどのビューはサポートされて、 **SQLGetInfo** SQL_INFO_SCHEMA_VIEWS オプションを使用します。 アプリケーションの実行をサポートされているビューからメタデータを取得する、**選択**スキーマに必要な情報を指定するステートメント。
