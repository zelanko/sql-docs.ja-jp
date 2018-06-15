---
title: 汎用アプリケーション |Microsoft ドキュメント
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
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae9643de106e11865505483d84f2253fb9511227
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909527"
---
# <a name="generic-applications"></a>汎用アプリケーション
汎用アプリケーションは、ことがあります、データベースからデータを取得するスプレッドシートなどのハードコーディングのタスクを実行します。 さまざまなユーザーを入力して SQL ステートメントを実行できるようにする、汎用クエリ アプリケーションなど、ユーザー定義のタスクを実行する場合もします。 どのような汎用アプリケーションが共通は、さまざまなさまざまな Dbms で動作する必要があります、開発者はわからない事前これら Dbms がどのようになるかです。  
  
 そのため、汎用アプリケーションは、高い相互運用できるようにする必要があります。 開発者は、機能の相互運用性を犠牲に多くの選択を行う必要があり、広範な機能をサポートするためにドライバーを必要とするコードを記述する必要があります。 一般的な Dbms を使用する汎用アプリケーションをチューニングする場合がありますがほとんど含まれているドライバー固有または DBMS に固有のコード。
