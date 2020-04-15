---
title: 相互運用可能なアプリケーションのテスト |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], testing interoperable applications
- testing interoperable applications [ODBC]
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1d43c7aad2501591c497475f6c250ac33712aa7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307743"
---
# <a name="testing-interoperable-applications"></a>相互運用可能なアプリケーションのテスト
相互運用可能なアプリケーションのテストは、最も時間のかかるビジネスであり、新しいドライバーが絶えず市場に出回るため、最悪の場合は不可能です。 ただし、合理的な程度のテストが可能です。 相互運用性が制限されているアプリケーションまたは相互運用性の低いアプリケーションは、サポートが保証されているドライバーに対してのみテストする必要があります。 ただし、これらのドライバーに対して完全にテストする必要があります。  
  
 相互運用性の高いアプリケーションは、すべてのドライバに対して実質的にテストすることはできません。 ほとんどのアプリケーション開発者ができる最善の方法は、少数のドライバに対して完全にテストし、さらに数台のドライバに対して慎重にテストすることです。 テストされたドライバーは、アプリケーションの市場で最も人気のある DBMS の最も人気のあるドライバーを含める必要があります。市場がすべての Dbms をカバーする場合は、デスクトップとサーバーの両方の DBMS のドライバーをテストする必要があります。  
  
 ODBC アプリケーションのテストで発生する問題の 1 つは、アプリケーション自体、ドライバー マネージャー、ドライバー、DBMS、ネットワーク ソフトウェアまたはゲートウェイなどのコンポーネントの数です。 アプリケーションは、ODBC 関数によって返されるエラー メッセージを**SQLGetDiagField および SQLGetDiagRec**を使用してポストすることで、エラーを追跡しやすくすることができます。 **SQLGetDiagRec** これらのメッセージは、エラーが発生した製造元とコンポーネントを識別します。 詳細については、[診断を](../../../odbc/reference/develop-app/diagnostics.md)参照してください。
