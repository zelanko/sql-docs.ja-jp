---
title: 垂直アプリケーション |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc88f38fd1ffe8b2ee0033ad0a2abc4f15fd5cf3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300377"
---
# <a name="vertical-applications"></a>垂直アプリケーション
垂直アプリケーションは、通常、1 つの DBMS に対して適切に定義されたタスクを実行します。 たとえば、受注入力アプリケーションは、会社の注文を追跡します。 これらのタイプのアプリケーションに共通しているのは、データベーススキーマは通常、アプリケーション開発者によって設計されており、アプリケーションは多くの異なるDBMSで動作する可能性がありますが、単一の顧客に対して単一のDBMSで動作します。  
  
 垂直アプリケーションでは通常、スクロール可能なカーソルやトランザクションなどの特定の機能が必要なため、すべての DBMS をサポートすることはほとんどありません。 代わりに、限られた DBMS のセット間で高度に相互運用できる傾向があります。 通常、垂直アプリケーション開発者は、市場の大部分を表す DBMS をサポートし、残りの部分を無視することを選択します。 テストと製品サポートのコストを削減するために、DBMSの特定のドライバをサポートすることもできます。  
  
 垂直アプリケーションは既知の DBMS のセットをサポートできるため、ドライバー固有のコードや DBMS 固有のコードが含まれている場合があります。 ただし、このようなコードは、維持に余分な時間を要するため、最小限に抑えるのが最善です。
