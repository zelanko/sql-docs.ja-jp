---
title: 垂直方向のアプリケーション |Microsoft Docs
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
ms.openlocfilehash: 6d0ed7a5f488765b56b2af0688ca14361590ab44
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022105"
---
# <a name="vertical-applications"></a>垂直アプリケーション
垂直アプリケーションは、通常、1つの DBMS に対して適切に定義されたタスクを実行します。 たとえば、注文エントリアプリケーションは、会社内の注文を追跡します。 これらの種類のアプリケーションでは、通常、データベーススキーマはアプリケーション開発者によって設計されていますが、アプリケーションはさまざまな Dbms で動作しますが、単一の顧客に対して1つの DBMS で動作します。  
  
 垂直アプリケーションでは通常、スクロール可能なカーソルやトランザクションなどの特定の機能が必要になるため、すべての Dbms がサポートされることはほとんどありません。 代わりに、Dbms の限られたセット間で高度な相互運用が可能になる傾向があります。 通常、垂直アプリケーション開発者は、市場の大部分を表す Dbms をサポートすることを選択し、残りは無視します。 また、これらの Dbms の特定のドライバーをサポートして、テストと製品サポートコストを削減することもできます。  
  
 垂直アプリケーションは、既知の一連の Dbms をサポートできるため、ドライバー固有または DBMS 固有のコードが含まれていることがあります。 ただし、このようなコードは、保守のために余分な時間が必要になるため、最小限に抑えることをお勧めします。
