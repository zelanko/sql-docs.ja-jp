---
title: "結果を受け取る |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a13be909891455c21b3409ea53072a5f2c9268e3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
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
