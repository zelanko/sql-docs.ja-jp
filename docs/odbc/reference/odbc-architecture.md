---
title: ODBC アーキテクチャ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07435dc1a5fbe800f2260e914f315cfe93dd8d1b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305133"
---
# <a name="odbc-architecture"></a>ODBC アーキテクチャ
ODBC アーキテクチャには、次の 4 つのコンポーネントがあります。  
  
-   **アプリケーション**処理を実行し、SQL ステートメントを送信し、結果を取得する ODBC 関数を呼び出します。  
  
-   **ドライバー マネージャー**アプリケーションの代わりにドライバーを読み込み、アンロードします。 ODBC 関数の呼び出しを処理するか、ドライバーに渡します。  
  
-   **ドライバー**ODBC 関数呼び出しを処理し、特定のデータ ソースに対して SQL 要求を送信し、結果をアプリケーションに返します。 必要に応じて、ドライバーは、要求が関連付けられた DBMS でサポートされている構文に準拠するようにアプリケーションの要求を変更します。  
  
-   **データ ソース**ユーザーがアクセスするデータと、DBMS にアクセスするために使用される関連するオペレーティング システム、DBMS、およびネットワーク プラットフォーム (存在する場合) で構成されます。  
  
 ODBC アーキテクチャに関する次の点に注意してください。 1 つ目は、複数のドライバーとデータ ソースが存在する可能性があり、これによりアプリケーションは複数のデータ ソースから同時にデータにアクセスできます。 次に、ODBC API は、アプリケーションとドライバー マネージャーの間、およびドライバー マネージャーと各ドライバーの間の 2 つの場所で使用されます。 ドライバ マネージャとドライバ間のインターフェイスは、*サービス プロバイダ インターフェイスまたは* *SPI*と呼ばれることもあります。 ODBC の場合、アプリケーション・プログラミング・インターフェース (API) とサービス・プロバイダー・インターフェース (SPI) は同じです。つまり、ドライバー マネージャーと各ドライバーは、同じ機能に同じインターフェイスを持っています。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [アプリケーション](../../odbc/reference/applications.md)  
  
-   [ドライバー マネージャー](../../odbc/reference/the-driver-manager.md)  
  
-   [ドライバー](../../odbc/reference/drivers.md)  
  
-   [データ ソース](../../odbc/reference/data-sources.md)
