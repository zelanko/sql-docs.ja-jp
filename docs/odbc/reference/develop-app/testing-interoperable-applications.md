---
title: 相互運用可能なアプリケーションのテスト |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], testing interoperable applications
- testing interoperable applications [ODBC]
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4cd98e6311d7d08b6faed0cb4759523642e70a5d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="testing-interoperable-applications"></a>相互運用可能なアプリケーションのテスト
相互運用可能アプリケーションのテストは、時間がかかる場合、最善でビジネスや市場で新しいドライバーが継続的に表示されるため、最悪の不可能です。 ただし、適度なテストができます。 制限付きまたは低の相互運用性を持つアプリケーションは、それらのドライバー サポートが保証されてに対してのみテストする必要があります。 ただし、する必要があります完全に比較するこれらのドライバーです。  
  
 高い相互運用可能アプリケーションは、すべてのドライバーに対して実質的にテストできません。 ほとんどのアプリケーション開発者が実行できる最も完全にドライバーの数が少ないと cursorily に対してさらにいくつかにテストを開始します。 テスト対象のドライバーは、アプリケーションの市場で最も一般的な Dbms の最も人気のあるドライバーを含める必要があります。市場では、すべての Dbms カバーしている場合は、デスクトップとサーバーの両方の Dbms 用のドライバーをテストしてください。  
  
 ODBC アプリケーションのテストの問題の 1 つは、関連するコンポーネントの数: アプリケーション自体、ドライバー マネージャー、ドライバー、DBMS および可能性のあるネットワーク ソフトウェアまたはゲートウェイ。 アプリケーションやすくを通じて ODBC 関数から返されたエラー メッセージを送信することによってエラーを追跡するために**SQLGetDiagField**と**SQLGetDiagRec**です。 これらのメッセージは、製造元とエラーが発生したコンポーネントを確認します。 詳細については、次を参照してください。[診断](../../../odbc/reference/develop-app/diagnostics.md)です。
