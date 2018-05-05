---
title: 相互運用可能なアプリケーションを作成する |Microsoft ドキュメント
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
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: 8b42b8ae-7862-4b63-a0b3-2a204e0c43a5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6aae50c316072c0970ffea4eb953f4e0ee86c5d5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="writing-an-interoperable-application"></a>相互運用可能なアプリケーションを作成します。
アプリケーションでは、1 つ以上のドライバーに対して同じコードを使用するたびにそのコードがこれらのドライバーの間で相互運用可能な場合があります。 ほとんどの場合、これは簡単な作業です。 たとえば、順方向専用カーソルに行をフェッチするコードは、すべてのドライバーは同じです。 場合によってより難しいこれができます。 たとえば、SQL ステートメントで使用するための識別子を構築するコードは、識別子の場合、引用符で囲む、および 1 つの要素、2 部構成、および 3 部構成の名前付け規則を考慮する必要があります。  
  
 一般に、相互運用可能なコードは、サポートされている機能と機能のばらつきの問題に対処する必要です。 *機能のサポート*は、特定の機能がサポートされているかどうかを参照します。 たとえば、すべて Dbms がトランザクションをサポートし、トランザクションのサポートに関係なく、相互運用可能なコードが正しく動作する必要があります。 *機能のばらつき*は、特定の機能がサポートされている方法でのバリエーションを参照します。 たとえば、カタログ名は、一部の Dbms の識別子の開始時に、他のユーザーの識別子の最後に配置されます。  
  
 アプリケーションは、デザイン時または実行時に、サポートされている機能と機能のばらつきが対処できます。 問題に対処する機能のサポートと可変性デザイン時に、開発者、ターゲットの Dbms とドライバーと調べ、同じコードをそれらの間の相互運用可能になることを確認します。 これは、一般に、低または制限付きの相互運用性とのアプリケーションが、これらの問題を処理する方法です。  
  
 たとえば、開発者は、垂直方向のアプリケーションが 4 つの特定の Dbms でのみ動作することを保証し、それらの Dbms の各トランザクションをサポートしている場合は、アプリケーションはの実行時にトランザクションのサポートを確認するためのコードは必要ありません。 常に、トランザクションをサポートするそれぞれの 4 つだけの Dbms を使用するデザイン時決定のため、トランザクションは使用が予想されます。  
  
 問題に対処する機能のサポートと可変性実行時に、アプリケーションが実行時にさまざまな機能をテストし、適宜動作し必要があります。 これは、一般に高い相互運用可能アプリケーションがこれらの問題を処理する方法です。 機能のサポートの問題、コードが利用できない場合、この機能をエミュレートする機能の省略可能または書き込みのコードを記述することを意味します。 つまり機能可変性問題の場合、使用可能なすべてのバリエーションをサポートするコードを記述します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [機能のサポートと可変性の確認](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [ウォッチする機能](../../../odbc/reference/develop-app/features-to-watch-for.md)
