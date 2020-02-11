---
title: ODBC アーキテクチャ |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 781a214d3ca059a442680c332d79aad48914976c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68111222"
---
# <a name="odbc-architecture"></a>ODBC アーキテクチャ
ODBC アーキテクチャには、次の4つのコンポーネントがあります。  
  
-   **アプリケーション**処理を実行し、ODBC 関数を呼び出して SQL ステートメントを送信し、結果を取得します。  
  
-   **ドライバーマネージャー**アプリケーションに代わってドライバーを読み込んでアンロードします。 ODBC 関数呼び出しを処理するか、ドライバーに渡します。  
  
-   **ドライバー**ODBC 関数呼び出しを処理し、SQL 要求を特定のデータソースに送信して、結果をアプリケーションに返します。 必要に応じて、ドライバーは、関連付けられている DBMS でサポートされている構文に準拠するように、アプリケーションの要求を変更します。  
  
-   **データソース**は、ユーザーがアクセスする必要があるデータと、DBMS にアクセスするために使用されるオペレーティングシステム、DBMS、およびネットワークプラットフォーム (存在する場合) で構成されます。  
  
 ODBC アーキテクチャについては、次の点に注意してください。 1つは、複数のドライバーとデータソースが存在し、アプリケーションが複数のデータソースのデータに同時にアクセスできるようにすることです。 2つ目の方法として、ODBC API は、アプリケーションとドライバーマネージャーの間、およびドライバーマネージャーと各ドライバーの間で使用されます。 ドライバーマネージャーとドライバーの間のインターフェイスは、*サービスプロバイダーインターフェイス (* *SPI*) と呼ばれることもあります。 ODBC の場合、アプリケーションプログラミングインターフェイス (API) と service provider interface (SPI) は同じです。つまり、ドライバーマネージャーと各ドライバーは、同じ機能に対して同じインターフェイスを持ちます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [[アプリケーション]](../../odbc/reference/applications.md)  
  
-   [ドライバー マネージャー](../../odbc/reference/the-driver-manager.md)  
  
-   [ドライバー](../../odbc/reference/drivers.md)  
  
-   [ソリューション エクスプローラー](../../odbc/reference/data-sources.md)
