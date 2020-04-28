---
title: 製品サイクルの長さ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], product cycle
- length of the product cycle [ODBC]
ms.assetid: 4d08d886-6d8b-40fd-8544-13032f4bf6c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d235146ffe1b4699f0064c5772407bcf40ae962
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306195"
---
# <a name="length-of-the-product-cycle"></a>製品サイクルの長さ
相互運用性に関する最後の質問は時間です。 相互運用可能なアプリケーションの開発は、通常、相互運用不可能なアプリケーションを開発するよりも時間がかかります。 その理由は、アプリケーションは DBMS の機能を確認し、さまざまな Dbms に対して同じタスクを異なる方法で実行する必要があるため、一部の Dbms ではサポートされている機能を回避できます。  
  
 開発時間に加えて、製品の有効期間を考慮する必要があります。 ある DBMS から別の DBMS への移行時にデータを転送するアプリケーションなど、アプリケーションを1回だけ使用するように設計されている場合、相互運用可能にするポイントはありません。 アプリケーションは一度だけ使用され、破棄されます。  
  
 アプリケーションが長期間存在する場合は、相互運用可能なアプリケーションとして保守が容易になることがあります。 これは、ターゲットとして1つの DBMS を持つカスタムアプリケーションにも当てはまります。 その理由は、相互運用可能なコードでは、データベース機能の限られたサブセットを使用するためです。 ドライバーは、基になる DBMS が変更された場合でも、これらの機能を使用可能な状態に保つために必要です。 そのため、相互運用可能なコードでは、DBMS に対する変更に対処する負担を、アプリケーション開発者からドライバー開発者に移行できます。
