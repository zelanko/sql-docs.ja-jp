---
title: 準備とコマンドを実行 |Microsoft ドキュメント
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
- Command object [ADO], preparing and executing commands
ms.assetid: 7448d9ee-7f4b-47e3-be54-2df8c9bbac32
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4d0736e2c4f0a09ec43f2e910cc7fd8c9263fc6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="preparing-and-executing-commands"></a>準備とコマンドの実行
コマンドは、基になるデータ ソースに対して操作を実行する、プロバイダーに発行された手順です。 たとえば、SQL ステートメントは、Microsoft SQL データ プロバイダーにコマンドです。 ADO では、コマンドは、通常によって表される**コマンド**もから簡単なコマンドを発行できますが、オブジェクト**接続**または**Recordset**オブジェクト。  
  
 使用することができます、**コマンド**プロバイダーがコマンド文字列を正しく解釈できることを想定して、プロバイダーからサポートされているあらゆる種類の操作を要求するオブジェクト。 データ プロバイダーの一般的な操作は、データベースをクエリ内のレコードを返す、 **Recordset**を考えられるの結果と、結果を表示するためのツールを保持するコンテナーとしてオブジェクト。 ADO オブジェクトの多くといくつか**コマンド**オブジェクトのコレクション、メソッド、またはプロパティは、プロバイダーの機能によって、参照されているときにエラーを生成可能性があります。  
  
 使用するだけでなく**コマンド**オブジェクトを使用することができます、 **Execute**メソッドを**接続**オブジェクトまたは**開く**メソッド**レコード セット**コマンドを実行して、それを実行するオブジェクト。 ただし、使用する必要があります、**コマンド**オブジェクトをコード内のコマンドを再利用する必要がある場合、またはコマンドにパラメーターの詳細な情報を渡す必要がある場合。 これらのシナリオはこのセクションで後で詳しく説明します。  
  
> [!NOTE]
>  特定**コマンド**s は結果をバイナリ ストリームとしてまたは 1 つのセットを返すことができます**レコード**ではなく同様、 **Recordset**プロバイダーでサポートされる場合は、します。 また、いくつか**コマンド**s が、結果セットに (たとえば、SQL Update クエリ) を返すものではありません。 このセクションで取り上げる、最も一般的なシナリオ、ただし: を実行する**コマンド**s として結果を返す、 **Recordset**オブジェクト。 結果を返すことの詳細については**レコード**s または**ストリーム**s」を参照してください[レコードとストリーム](../../../ado/guide/data/records-and-streams.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Command オブジェクトの概要](../../../ado/guide/data/command-object-overview.md)  
  
-   [簡単なコマンドの作成と実行](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command オブジェクトのパラメーター](../../../ado/guide/data/command-object-parameters.md)  
  
-   [Command を使用してストアド プロシージャを呼び出す](../../../ado/guide/data/calling-a-stored-procedure-with-a-command.md)  
  
-   [接続オブジェクトのメソッドとしてストアド プロシージャの呼び出し](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
-   [名前付きコマンド](../../../ado/guide/data/named-commands.md)  
  
-   [名前付きコマンドにパラメーターを渡す](../../../ado/guide/data/passing-parameters-to-a-named-command.md)
