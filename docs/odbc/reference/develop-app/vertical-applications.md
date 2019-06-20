---
title: 垂直アプリケーション |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df7a2d036692cefcd1b2ea2338d51938a11ea85a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208408"
---
# <a name="vertical-applications"></a>垂直アプリケーション
垂直方向のアプリケーションは、通常 1 つの DBMS に対して明確に定義されたタスクを実行します。 たとえば、受注アプリケーションは、会社に注文を追跡します。 どのようなアプリケーションのこれらの型が共通は、データベース スキーマは、通常、アプリケーション開発者が設計されています、さまざまな Dbms の数が、アプリケーションが動作可能性があります、機能、1 つの DBMS で単一の顧客のです。  
  
 垂直方向のアプリケーションでは、スクロール可能なカーソルやトランザクションなど、特定の機能は、通常必要なためほとんどすべての Dbms をサポートします。 代わりに、限られた数の Dbms の間で高い相互運用できるようにする傾向があります。 通常、垂直方向のアプリケーション開発者は、市場の大部分を表し、残りの部分を無視するこれらの Dbms をサポートするために選択します。 これらのテストを削減する Dbms と製品のサポート コストの特定のドライバーをサポートする場合がありますも選択します。  
  
 垂直方向のアプリケーションでは、既知の Dbms のセットをサポートできますが、ため、ドライバー固有または DBMS 固有のコードも含まれます。 ただし、このようなコードが最適なを最小限に抑える余分な時間を維持する必要があるためです。
