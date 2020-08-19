---
description: エラーの予測
title: エラーの予測 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- anticipating errors [ADO]
- errors [ADO], preventing
- preventing errors [ADO]
ms.assetid: ea1d4a97-58c3-476b-a496-cc80db2a90d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 799a238d37e7b2fe4f5f4c8af5bb396513b75b03
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453734"
---
# <a name="anticipating-errors"></a>エラーの予測
エラーの防止は、少なくともエラー処理と同じです。 この最後のセクションでは、エラーが発生する可能性が低くなるようにアプリケーションが実行できる予防措置の一覧を示します。  
  
 オブジェクトの状態を確認するには、そのオブジェクトを使用して操作を実行する前に **state** プロパティの値を確認します。 たとえば、アプリケーションがグローバル**接続**を使用している場合は、 **open**メソッドを呼び出す前に、その**状態**プロパティをチェックして、既に開いているかどうかを確認します。  
  
-   ユーザーからのデータを受け入れるプログラムには、データストアに送信する前にデータを検証するコードを含める必要があります。 データストア、プロバイダー、ADO、またはプログラミング言語に依存して、問題を通知することはできません。 ユーザーが入力したすべてのバイトを確認し、データがフィールドの正しい型であること、および必要なフィールドが空でないことを確認する必要があります。  
  
 データをデータストアに書き込む前に、データを確認してください。 これを行う最も簡単な方法は、WillUpdateRecordset**イベントを**処理すること**WillUpdateRecordset**です。 ADO イベントの処理の詳細については、「 [Ado イベントの処理](../../../ado/guide/data/handling-ado-events.md)」を参照してください。  
  
 レコードポインターの移動を試行する前に、レコード **セット** オブジェクトがレコード **セット** の境界を超えていないことを確認してください。 **EOF**が true のとき、または**BOF**が True のときに**MovePrev**を**MoveNext**にしようとすると、エラーが発生します。 **EOF**と**BOF**の両方が True の場合に**Move**メソッドを実行すると、エラーが生成されます。  
  
 また、空の**レコードセット**に対して**Seek**や**Find**などの操作を実行しようとすると、エラーが発生します。
