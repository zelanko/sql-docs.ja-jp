---
title: 結果を受け取る |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3330d2989f5662693ff7aca720d2bf6e07e16e33
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="receiving-results"></a>結果を受信
ADO ではほとんどのコマンドは、呼び出し元に返される一部の情報とは、します。 行セットを返すコマンドの結果の受信、**レコード セット**はおそらく、最も使用されている ADO オブジェクトのオブジェクト。  
  
 いくつかの方法でデータを受信する、 **Recordset**オブジェクトを次の呼び出しなど、データ ソースから。  
  
-   [Connection.Execute メソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command.Execute メソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Recordset.Open メソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection.NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [Connection.StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 内のデータを受信、 **Recordset**オブジェクトでの参加による、データの取得のプロセスは終了、**接続**オブジェクトおよび**コマンド**オブジェクトを暗黙的にまたは明示的にします。 システムでは、一般的なクライアント/サーバー アプリケーション、データの取得のプロセス全体が必要です、ラウンド トリップ ネットワーク経由で入力ごとに**Recordset**です。  
  
 1 つ以上の結果セットを受信する手段がいくつか作成する必要がありますのラウンド トリップにカプセル化されたデータ セットごとに 1 つ、ネットワーク経由で、 **Recordset**オブジェクト。 低速か混雑しているネットワークでは、ラウンド トリップの数を減らすために役立つアプリケーションのパフォーマンスを向上させます。 一部のプロバイダーが複数の受信には、サポートを提供するそのため、 **Recordset**1 回のラウンド トリップで s。 これは、次のトピックについて説明します。  
  
-   [複数のレコードセットの受信](../../../ado/guide/data/receiving-multiple-recordsets.md)
