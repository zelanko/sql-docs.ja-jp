---
title: 図形は一般にコマンド |Microsoft ドキュメント
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
- shape commands [ADO]
- data shaping [ADO], shape commands
ms.assetid: 1fac7831-a187-4b15-9b43-aad380c5556c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2b0998c905e286063cdec6fce3c98f8be2b6937
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="shape-commands-in-general"></a>一般的な図形コマンド
形の列を定義するデータの整形**Recordset**、列、および方法によって表されるエンティティ間のリレーションシップ、**レコード セット**データが格納されます。  
  
 形状**Recordset**次の種類の列で構成できます。  
  
|列の型|Description|  
|-----------------|-----------------|  
|data|フィールド、 **Recordset**データ プロバイダーには、クエリ コマンドによって返される、テーブル、または以前の形**Recordset**です。|  
|章|相互に参照**Recordset**という、*章*です。 チャプター列を作成することを定義すること、*親子*リレーションシップ場所、*親*は、 **Recordset**チャプター列と、を含む*子*は、 **Recordset**章によって表されます。|  
|集計 (aggregate)|実行することによって、列の値が派生した、*集計関数*のすべての行または子のすべての行の列で**レコード セット**です。 (次のトピックでは、集計関数を参照してください[集計関数、CALC 関数と NEW キーワード](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md))。|  
|計算式|Visual Basic アプリケーションの同じ行に列の式を計算することで、列の値が派生した、 **Recordset**です。 式では計算関数の引数です。 (次のトピックの計算式を参照して[集計関数、CALC 関数と NEW キーワード](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md)し、[アプリケーション関数の Visual Basic](../../../ado/guide/data/visual-basic-for-applications-functions.md))。|  
|新機能|空で作成されるフィールドを後でデータを設定することができます。 列は、NEW キーワードで定義されます。 (次のトピックでは、新しいキーワードを参照してください[集計関数、CALC 関数と NEW キーワード](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md))。|  
  
 Shape コマンドから返される基になるデータ プロバイダーをクエリ コマンドを指定する句を含めることができます、 **Recordset**オブジェクト。 クエリの構文は、基になるデータ プロバイダーの要件によって異なります。 これは、場合、通常は SQL では、ADO では、特定のクエリ言語の使用は必要ありません。  
  
 図形のコマンドを発行できる**Recordset**オブジェクトか、設定、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)のプロパティ、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトと呼び出すことで、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドです。  
  
 SQL の JOIN 句を使用して 2 つのテーブルを関連付けるただし、階層**Recordset**より効率的に情報を表すことができます。 行ごと、 **Recordset**一方のテーブルから重複して参加繰り返し情報によって作成します。 階層**Recordset**のみ 1 つの親を持つ**レコード セット**複数の子の各**レコード セット**オブジェクト。  
  
 図形のコマンドは、入れ子にすることができます。 つまり、*親コマンド*または*子コマンド*別の図形コマンド自体する可能性があります。  
  
 Shape プロバイダーは、ユーザーのカーソル位置を指定する場合でも常に、クライアント カーソルを返します**adUseServer**です。  
  
 アクセスすることができます、**レコード セット**形状のコンポーネント**Recordset**プログラムまたは適切なビジュアル コントロール。  
  
 マイクロソフトは、図形のコマンドを生成するためのビジュアル ツールを提供しています (を参照してください、[データ環境デザイナー](http://go.microsoft.com/fwlink/?LinkId=5689) Visual Basic 6 マニュアルを参照) と、階層のカーソル (を参照してください"を使用して、Microsoft 階層を表示します。フレキシブル グリッド コントロール"、Visual Basic 6 マニュアルを参照)。  
  
 階層を移動する方法について**Recordset**を参照してください[階層レコード セット内の行へのアクセス](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)です。  
  
 構文的に正しい図形コマンドに関する正確な情報は、次を参照してください。[図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [集計関数、CALC 関数、NEW キーワード](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md)  
  
-   [基になるデータ プロバイダーにコマンドを発行する](../../../ado/guide/data/issuing-commands-to-the-underlying-data-provider.md)
