---
title: スキーマ ビュー |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304253"
---
# <a name="schema-views"></a>スキーマ ビュー
アプリケーションは、ODBC カタログ関数を呼び出すか、INFORMATION_SCHEMAビューを使用して、DBMS からメタデータ情報を取得できます。 ビューは、ANSI SQL-92 標準によって定義されます。  
  
 DBMS とドライバーでサポートされている場合、INFORMATION_SCHEMA ビューは、ODBC カタログ関数が提供するよりも、メタデータをより強力かつ包括的に取得する手段を提供します。 アプリケーションは、これらのビューのいずれかに対して独自のカスタム**SELECT**ステートメントを実行したり、ビューを結合したり、ビューに対してユニオンを実行したりできます。 より大きなユーティリティとメタデータの広い範囲を提供しながら、INFORMATION_SCHEMAビューは、多くの場合、DBMSでサポートされていません。 これは、より多くの DBMS とドライバーが SQL-92 に準拠するにつれて変更される可能性があります。  
  
 サポートされているビューを特定するには、アプリケーションはSQL_INFO_SCHEMA_VIEWS オプションを指定して**SQLGetInfo**を呼び出します。 サポートされているビューからメタデータを取得するために、アプリケーションは必要なスキーマ情報を指定する**SELECT**ステートメントを実行します。
