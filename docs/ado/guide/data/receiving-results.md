---
description: 結果の受信
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3317441322d0f1be94ee1c897946d83f6291143c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452994"
---
# <a name="receiving-results"></a>結果の受信
ADO のほとんどのコマンドでは、呼び出し元に返される情報がいくつかあります。 行セットを返すコマンドの場合、結果は **レコードセット** オブジェクトで受信されます。これは、おそらく ADO オブジェクトで最もよく使用されています。  
  
 データソースから **レコードセット** オブジェクトのデータを受信するには、次のようないくつかの方法があります。  
  
-   [Connection.Exeかわいらしいメソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command.Exeかわいらしいメソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Recordset. Open メソッド](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [接続. NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [接続. StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 **レコードセット**オブジェクトでデータを受信すると、**接続**オブジェクトと**コマンド**オブジェクトが暗黙的または明示的に関与して、データを取得するプロセスが終了します。 一般的なクライアント/サーバーアプリケーションシステムでは、データを取得するプロセス全体で、入力された **レコードセット**ごとにネットワーク経由でラウンドトリップが必要になります。  
  
 複数の結果セットを受け取るには、 **レコードセット** オブジェクトにカプセル化されたデータセットごとに1つずつ、ネットワーク経由で複数のラウンドトリップを行う必要があります。 低速または混雑しているネットワークの場合、ラウンドトリップの数を減らすと、アプリケーションのパフォーマンスが向上する可能性があります。 そのため、一部のプロバイダーでは、1回のラウンドトリップで複数の **レコードセット**を受け取ることがサポートされています。 これについては、次のトピックで説明します。  
  
-   [複数のレコードセットの受信](../../../ado/guide/data/receiving-multiple-recordsets.md)
