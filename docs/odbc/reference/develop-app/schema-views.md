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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a1a9e421c4835d35e3c4f3c644e69b8c7601e8e4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304253"
---
# <a name="schema-views"></a>スキーマ ビュー
アプリケーションでは、ODBC カタログ関数を呼び出すか INFORMATION_SCHEMA ビューを使用することによって、DBMS からメタデータ情報を取得できます。 ビューは ANSI SQL-92 標準で定義されています。  
  
 DBMS とドライバーでサポートされている場合、INFORMATION_SCHEMA ビューでは、ODBC カタログ関数が提供するよりも強力で包括的な方法でメタデータを取得できます。 アプリケーションは、これらのビューのいずれかに対して独自のカスタム**SELECT**ステートメントを実行したり、ビューを結合したり、ビューに対して union を実行したりできます。 より多くのユーティリティを提供し、メタデータの範囲を広げる一方で、INFORMATION_SCHEMA ビューは DBMS ではサポートされません。 これは、Dbms とドライバーが SQL-92 に準拠するようになるにつれて変わる可能性があります。  
  
 アプリケーションでは、サポートされているビューを特定するために、SQL_INFO_SCHEMA_VIEWS オプションを使用して**SQLGetInfo**を呼び出します。 サポートされているビューからメタデータを取得するために、アプリケーションは必要なスキーマ情報を指定する**select**ステートメントを実行します。
