---
title: "製品サイクルの長さ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], product cycle
- length of the product cycle [ODBC]
ms.assetid: 4d08d886-6d8b-40fd-8544-13032f4bf6c7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c363ecd47545868e2d40afabdce9bbef6f78031
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="length-of-the-product-cycle"></a>製品サイクルの長さ
相互運用性に関する最終的な質問は、時間です。 Noninteroperable の 1 つの開発よりも時間がかかります通常相互運用可能なアプリケーションを開発します。 理由は、アプリケーションする必要があります DBMS の機能を確認、さまざまな Dbms の異なる方法で、同じ操作を実行、Dbms によってのみでサポートされる機能を回避するなどです。  
  
 開発時だけでなく、製品の有効期間を考慮する必要があります。 間、1 つの DBMS から移行する場合は、データを転送するアプリケーションなど、1 回使用するアプリケーションが設計されている場合、相互運用可能なことでポイントはありません。 アプリケーションは 1 回使用され、破棄されます。  
  
 アプリケーション時間が長く存在する場合、相互運用可能なアプリケーションとして管理しやすく場合があります。 これはターゲットとして 1 つの DBMS を持つカスタム アプリケーションにも当てはまります。 その理由は、相互運用可能なコードがデータベース機能の限定されたサブセットを使用します。 基になる DBMS の変更が発生した場合でも、使用できる機能を保持するには、ドライバーが必要です。 したがって、相互運用可能なコードの変更に対処する負担を移動、DBMS アプリケーション開発者はドライバーの開発者からです。

