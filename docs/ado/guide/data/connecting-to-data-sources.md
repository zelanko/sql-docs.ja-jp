---
title: データソースへの接続 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: rothja
ms.author: jroth
ms.openlocfilehash: 1ef641bbfb94b8fde5f12af6cadd03f13fbfa91f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761168"
---
# <a name="connecting-to-data-sources"></a>データ ソースへの接続
ADO**接続**オブジェクトは、DBMS、ファイルストア、またはコンマ区切りのテキストファイルを含む、データソースとの一意のセッションを表します。 クライアント/サーバーデータベースシステムの場合、ADO 接続はサーバーへの実際のネットワーク接続にすることができます。  
  
 接続**オブジェクトは**、接続構成の指定、接続の開始と終了、データソースに対するコマンドの作成と実行、および基になるデータソースのデザインに関する情報のスキーマ行セットの形式での提供など、さまざまな[プロパティとメソッド](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)をサポートしています。プロバイダーでサポートされている機能によっては、**接続**オブジェクトの一部のコレクション、メソッド、またはプロパティが使用できないことがあります。  
  
 **接続**オブジェクトを使用するか、**レコードセット**オブジェクトを使用して、データソースに接続できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [接続オブジェクトを使用する](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [レコードセット オブジェクトを使用する](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [接続文字列の作成](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [接続プロパティの指定](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [トランザクションの制御](../../../ado/guide/data/controlling-transactions-ado.md)
