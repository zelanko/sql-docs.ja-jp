---
title: "垂直方向アプリケーション |Microsoft ドキュメント"
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
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ce78adb6af76ff17b6df0e0ecc910f1266bf7dea
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="vertical-applications"></a>垂直方向のアプリケーション
垂直方向のアプリケーションは、通常 1 つの DBMS に対して適切に定義されたタスクを実行します。 たとえば、受注アプリケーションは、会社内の注文を追跡します。 どのようなアプリケーションのこれらの型が共通は、データベース スキーマは通常、アプリケーション開発者によってに設計された、アプリケーションは、さまざまな Dbms の数が動作可能性があります中、それと共に単一 DBMS 1 人の顧客のです。  
  
 垂直方向のアプリケーションでは、スクロール可能なカーソルやトランザクションなどの特定の機能では、通常必要なためすべて Dbms ほとんどサポートします。 代わりに、限られた一連の Dbms の間で高い相互運用できるように、傾向があります。 通常、垂直方向アプリケーション開発者は、市場の大規模な分数を表し、残りの部分を無視するそれらの Dbms をサポートするために選択します。 これらのテストを削減する Dbms および製品のサポート コストを特定のドライバーをサポートするためもできます。  
  
 垂直方向のアプリケーションでは、既知の Dbms のセットをサポートできますがので、場合によって、格納されるドライバー固有または DBMS に固有のコード。 ただし、このようなコードは、最適なを最小限にとどめるが維持するために余分な時間が必要です。
