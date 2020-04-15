---
title: 汎用アプリケーション |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607676d5370f02ee1d39196bff9261bc897521ee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305553"
---
# <a name="generic-applications"></a>汎用アプリケーション
汎用アプリケーションは、データベースからデータを取得するスプレッドシートなどのハードコーディングされたタスクを実行することがあります。 また、汎用クエリ アプリケーションなど、さまざまなユーザー定義タスクを実行して、ユーザーが SQL ステートメントを入力して実行できるようにする場合もあります。 共通する一般的なアプリケーションは、さまざまな DBMS を使用する必要があり、開発者はこれらの DBMS がどうなるかを事前に知らないということです。  
  
 そのため、汎用アプリケーションは高度に相互運用できる必要があります。 開発者は多くの選択肢を作成し、機能の相互運用性をトレードオフし、ドライバーが幅広い機能をサポートすることを期待するコードを記述する必要があります。 汎用アプリケーションは、一般的な DBMS で動作するように調整される場合がありますが、ドライバー固有のコードや DBMS 固有のコードが含まれることはほとんどありません。
