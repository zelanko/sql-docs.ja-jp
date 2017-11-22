---
title: "データ ソースへの接続 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a05c4da49edef0635e95cc5aaf43976ff0753af
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="connecting-to-data-sources"></a>データ ソースへの接続
ADO**接続**オブジェクトは、DBMS、ファイル ストア、またはコンマ区切りのテキスト ファイルを含む、データ ソースの一意のセッションを表します。 クライアント/サーバー データベース システムでは、ADO 接続はサーバーへの実際のネットワーク接続を指定できます。  
  
 **接続**オブジェクトがサポートするさまざまな[プロパティとメソッド](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)を開くと接続を閉じる、作成および実行で、データ ソースに対してコマンドを接続構成を指定するには、、およびなどに、基になるデータ ソース スキーマ行セットの形式での設計に関する情報を提供します。プロバイダー、いくつかのコレクション、メソッド、またはのプロパティがサポートする機能によって、**接続**オブジェクトを使用できない可能性があります。  
  
 使用するか、データ ソースに接続することができます、**接続**オブジェクト、またはを使用して、 **Recordset**オブジェクト。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [接続オブジェクトを使用する](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [レコードセット オブジェクトを使用する](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [接続文字列の作成](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [接続プロパティの指定](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [トランザクションを制御します。](../../../ado/guide/data/controlling-transactions-ado.md)
