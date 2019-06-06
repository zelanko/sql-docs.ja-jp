---
title: 結果の受信 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: edd070cc6f10829b597534d024d767de2a0c7e12
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701713"
---
# <a name="receiving-results"></a>結果の受信
ADO ではほとんどのコマンドは、呼び出し元に返される情報はいくつかの結果します。 行セットを返すコマンドの結果を受信してで、**レコード セット**でおそらく、最も使用されている ADO オブジェクトのあるオブジェクト。  
  
 いくつかの方法でデータを受信する、 **Recordset**次の呼び出しなど、データ ソースからのオブジェクト。  
  
-   [Connection.Execute メソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command.Execute メソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Recordset.Open メソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection.NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [Connection.StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 内のデータの受信、**レコード セット**オブジェクトでの参加で、データの取得のプロセスは終了です、**接続**オブジェクトと**コマンド**オブジェクトを暗黙的にまたは明示的にします。 一般的なクライアント/サーバー アプリケーション システムでのデータの取得のプロセス全体が必要ですラウンド トリップ ネットワーク経由で入力ごとに**Recordset**します。  
  
 カプセル化されている各データ セットのいずれかと、ネットワーク経由でいくつかのようにすることになることを意味ラウンド トリップを 1 つ以上の結果セットが表示される、 **Recordset**オブジェクト。 低速または混雑しているネットワークでは、ラウンド トリップの数を減らすことに役立つアプリケーションのパフォーマンスを向上します。 一部のプロバイダーが複数の受信のサポートを提供するそのため、 **Recordset**1 回のラウンド トリップで s。 これは、次のトピックについて説明します。  
  
-   [複数のレコードセットの受信](../../../ado/guide/data/receiving-multiple-recordsets.md)
