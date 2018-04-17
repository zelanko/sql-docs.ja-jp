---
title: ブロック カーソル、スクロール可能なカーソルとの下位互換性 |Microsoft ドキュメント
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
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e25e546b359dd7178739e074664c3239fcfbdba
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>ブロック カーソル、スクロール可能なカーソル、および旧バージョンとの互換性
両方の存在**SQLFetchScroll**と**SQLExtendedFetch** ODBC の間で、アプリケーション プログラミング インターフェイス (API)、これは、一連の関数の最初のクリアが分割を表します、アプリケーションの呼び出し、およびサービス プロバイダー インターフェイス (SPI) の関数のセットからなるドライバーを実装します。 この分割が必要なように ODBC 3 です。*x*が使用される**SQLFetchScroll**、標準に bealigned も ODBC 2 と互換性があるとします*。x*が使用される**SQLExtendedFetch**です。  
  
 ODBC 3*.x*は API のセットがアプリケーションの呼び出しの機能にも含まれます**SQLFetchScroll**に関連するステートメント属性とします。 ODBC 3*.x*セットからなる SPI 関数のドライバーを実装して、含まれています**SQLFetchScroll**、 **SQLExtendedFetch**、関連するステートメント属性とします。 ODBC は、API と SPI がこのような単位に分割を正式には適用しません、ため、ODBC 3 可能性が*.x*アプリケーションを呼び出す**SQLExtendedFetch**に関連するステートメント属性とします。 ただし、ODBC 3 の理由はありません*.x*これを行うアプリケーション。 Api および Spi の詳細については、の紹介」を参照してください。 [ODBC アーキテクチャ](../../../odbc/reference/odbc-architecture.md)です。  
  
 どのような関数とステートメントについては、ODBC 3 属性します。*x*アプリケーションがブロックとスクロール可能なカーソルを使用する必要がありますを参照してください[ブロック カーソル、スクロール可能なカーソル、および ODBC 3.x アプリケーションとの下位互換性](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバー マネージャーの機能](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [ドライバーの機能](../../../odbc/reference/appendixes/what-the-driver-does.md)
