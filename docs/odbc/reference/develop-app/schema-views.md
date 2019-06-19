---
title: スキーマ ビュー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 782dec08b76a9e5a97719d6af39e2c30c0f92d19
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62468619"
---
# <a name="schema-views"></a>スキーマ ビュー
ODBC カタログ関数を呼び出すことによって、または INFORMATION_SCHEMA ビューを使用して、アプリケーションは、DBMS からメタデータ情報を取得できます。 ビューは、ANSI sql-92 標準で定義されます。  
  
 DBMS とドライバーでサポートされる、INFORMATION_SCHEMA ビューは、ODBC カタログ関数のメタデータを取得するより強力で包括的な手段を提供します。 アプリケーションが独自のカスタムを実行できる**選択**に対してこれらのビューのいずれかのステートメントは、ビューに参加できますまたはビューに対して和集合を実行することができます。 大きいユーティリティおよび広範なメタデータを提供しながら INFORMATION_SCHEMA ビューは、DBMS によって多くの場合、サポートされていません。 これは、Dbms とドライバーの詳細については、SQL 92 とへの準拠を実現するように変更する可能性があります。  
  
 アプリケーションを呼び出すビューがサポートされているかを判断する**SQLGetInfo** SQL_INFO_SCHEMA_VIEWS オプションを使用します。 サポートされているビューからのメタデータを取得するアプリケーションが実行される、**選択**ステートメントに必要なスキーマ情報を指定します。
