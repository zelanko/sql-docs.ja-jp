---
title: スキーマビュー |Microsoft Docs
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
ms.openlocfilehash: 1e2dd512ab529f1fb5d216f4a2e459cd601d40e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67943755"
---
# <a name="schema-views"></a>スキーマ ビュー
アプリケーションでは、ODBC カタログ関数を呼び出すか INFORMATION_SCHEMA ビューを使用することによって、DBMS からメタデータ情報を取得できます。 ビューは ANSI SQL-92 標準で定義されています。  
  
 DBMS とドライバーでサポートされている場合、INFORMATION_SCHEMA ビューでは、ODBC カタログ関数が提供するよりも強力で包括的な方法でメタデータを取得できます。 アプリケーションは、これらのビューのいずれかに対して独自のカスタム**SELECT**ステートメントを実行したり、ビューを結合したり、ビューに対して union を実行したりできます。 より多くのユーティリティを提供し、メタデータの範囲を広げる一方で、INFORMATION_SCHEMA ビューは DBMS ではサポートされません。 これは、Dbms とドライバーが SQL-92 に準拠するようになるにつれて変わる可能性があります。  
  
 アプリケーションでは、サポートされているビューを特定するために、SQL_INFO_SCHEMA_VIEWS オプションを使用して**SQLGetInfo**を呼び出します。 サポートされているビューからメタデータを取得するために、アプリケーションは必要なスキーマ情報を指定する**select**ステートメントを実行します。
