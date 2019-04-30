---
title: 相互運用可能なアプリケーションの作成 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: 8b42b8ae-7862-4b63-a0b3-2a204e0c43a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e559eab5787a64b6bdf0850147d7d9128fc435c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208580"
---
# <a name="writing-an-interoperable-application"></a>相互運用可能なアプリケーションの作成
アプリケーションでは、1 つ以上のドライバーに対して同じコードを使用するたびにそのコードがそれらのドライバーの間で相互運用可能な場合があります。 ほとんどの場合、これは、簡単な作業です。 たとえば、順方向専用カーソルに行をフェッチするコードは、すべてのドライバーは同じです。 場合によっては、難しくこれができます。 たとえば、SQL ステートメントで使用するための識別子を構築するコードは、識別子の場合、引用符で囲む、1 部、2 つの部分、および 3 つの部分の名前付け規則を考慮する必要があります。  
  
 一般に、相互運用可能なコードは、サポートされている機能と機能の可変性の問題に対処する必要があります。 *機能のサポート*特定の機能がサポートされているかどうかを参照します。 たとえば、トランザクションをサポートするすべての Dbms と相互運用可能なコードは、トランザクションのサポートに関係なく正しく動作する必要があります。 *機能の可変性*と特定の機能がサポートされている方法での差異を指します。 たとえば、カタログ名は、一部の Dbms の識別子の開始時および他のユーザーの識別子の末尾に配置されます。  
  
 アプリケーションは、デザイン時または実行時に、機能のサポートと可変性の機能を処理できます。 デザイン時に、機能のサポートと可変性処理をするには、開発者ターゲット Dbms とドライバーでは、同じコードになるはそれらの間で相互運用可能なことを確認します。 これは、一般を低または制限付きの相互運用性とアプリケーションがこれらの問題を処理する方法です。  
  
 たとえば、開発者垂直方向のアプリケーションが 4 つの特定の Dbms でのみ動作することを保証し、これらの Dbms のトランザクションをサポートする場合は、アプリケーションは実行時にトランザクションのサポートをチェックするコードは必要ありません。 常に、トランザクションがトランザクションをサポートするそれぞれの 4 つだけの Dbms を使用するデザイン時かにより使用が予想されます。  
  
 対処する機能のサポートと可変性実行時に、アプリケーションは実行時にさまざまな機能をテストし、それに従って動作する必要があります。 これは、一般に、これらの問題での高い相互運用可能なアプリケーションの処理方法です。 機能のサポートの問題、コードが利用できない場合、この機能をエミュレートする機能の省略可能または書き込みのコードを記述することを意味します。 機能のばらつき問題、可能性のあるすべてのバリエーションをサポートするコードの記述を意味します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [機能のサポートと可変性の確認](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [ウォッチする機能](../../../odbc/reference/develop-app/features-to-watch-for.md)
