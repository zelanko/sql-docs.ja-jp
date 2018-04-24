---
title: データ ソースへの接続 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc1f10e8ceae959927ab2a7b42db800ef140892f
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
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
