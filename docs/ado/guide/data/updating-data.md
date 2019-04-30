---
title: データの更新 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d593bd3ad745f316b833b375ceaae8b764d21ec2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184986"
---
# <a name="updating-data"></a>データの更新
更新プログラムの動作と機能に大きく依存モード (ロックの種類)、カーソルの種類、およびカーソルの場所を更新します。  
  
 使用して、 **Update**の現在のレコードに加えた変更を保存する方法、**レコード セット**オブジェクトを呼び出した後、 **AddNew**メソッドまたは任意のフィールドの値を変更した後で既存のレコード。 **Recordset**オブジェクトは、更新プログラムをサポートする必要があります。  
  
 場合、 **Recordset**オブジェクトは、バッチ更新をサポートしているを呼び出すまで、ローカルでは、1 つまたは複数のレコードに複数の変更をキャッシュすることができます、 **UpdateBatch**メソッド。 現在のレコードを編集または呼び出すときに新しいレコードを追加する場合、 **UpdateBatch**メソッド、ADO の呼び出しが自動的に、 **Update**メソッドの前に、現在のレコードに保留中の変更を保存するにはプロバイダーにバッチ処理された変更を送信します。  
  
 現在のレコードを呼び出した後は、最新の状態、 **Update**または**UpdateBatch**メソッド。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [イミディエイト モード](../../../ado/guide/data/immediate-mode.md)  
  
-   [バッチ モード](../../../ado/guide/data/batch-mode.md)  
  
-   [トランザクション処理 ](../../../ado/guide/data/transaction-processing.md)
