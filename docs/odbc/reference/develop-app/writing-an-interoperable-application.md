---
title: 相互運用可能なアプリケーションを作成する |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 553e718e0759e47701e7f8c04561693358d5dc52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289084"
---
# <a name="writing-an-interoperable-application"></a>相互運用可能なアプリケーションの作成
アプリケーションが複数のドライバーに対して同じコードを使用する場合は、そのコードがそれらのドライバー間で相互運用可能である必要があります。 ほとんどの場合、これは簡単な作業です。 たとえば、前方専用カーソルを持つ行をフェッチするコードは、すべてのドライバーで同じです。 場合によっては、これはより困難になる可能性があります。 たとえば、SQL ステートメントで使用する識別子を作成するコードでは、識別子の大文字と小文字、引用符、および 1 部構成、2 部構成、および 3 部構成の命名規則を考慮する必要があります。  
  
 一般に、相互運用可能なコードは、機能のサポートと機能の変動の問題に対処する必要があります。 *機能のサポート*とは、特定の機能がサポートされているかどうかを示します。 たとえば、すべての DBMS がトランザクションをサポートしているわけではないので、トランザクションサポートに関係なく相互運用可能なコードが正しく動作する必要があります。 *特徴の変動性*とは、特定の機能がサポートされる方法の変化を指します。 例えば、カタログ名は、一部の DBMS の ID の先頭に置かれ、他の DBMS では ID の最後に置かれます。  
  
 アプリケーションは、設計時または実行時に機能のサポートと機能の変動に対処できます。 デザイン時の機能サポートと可変性に対処するために、開発者はターゲットの DBMS とドライバを調べ、それらの間で同じコードが相互運用可能であることを確認します。 これは、一般に、相互運用性の低いアプリケーションや限られたアプリケーションがこれらの問題に対処する方法です。  
  
 たとえば、開発者が垂直アプリケーションが 4 つの特定の DBMS でのみ動作することを保証し、それらの DBMS のそれぞれがトランザクションをサポートする場合、アプリケーションは実行時にトランザクションのサポートをチェックするコードを必要としません。 トランザクションをサポートする 4 つの Dbms のみを使用するという設計時の決定により、トランザクションが使用可能であると常に想定できます。  
  
 実行時に機能のサポートと変動性に対処するには、アプリケーションは実行時に異なる機能をテストし、それに応じて対応する必要があります。 これは一般的に、相互運用性の高いアプリケーションがこれらの問題に対処する方法です。 機能サポートの問題の場合、これは、機能をオプションにするコードを記述するか、または機能が使用できないときにその機能をエミュレートするコードを記述することを意味します。 機能の変動性の問題に対しては、すべてのバリエーションをサポートするコードを記述することを意味します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [機能のサポートと可変性の確認](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [ウォッチする機能](../../../odbc/reference/develop-app/features-to-watch-for.md)
