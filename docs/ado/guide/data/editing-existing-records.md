---
title: 既存のレコードを編集 |Microsoft ドキュメント
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
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43faf0a4bd21513bd03f89814cdb03fd55347bc4
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="editing-existing-records"></a>既存のレコードの編集
既存のレコードを編集するには、編集し、変更する行に移動、**値**を変更するフィールドのプロパティです。 詳細については、**フィールド**オブジェクトの**値**プロパティを参照してください[データを調べる](../../../ado/guide/data/examining-data.md)です。 使用する、カーソルの種類に応じて、**更新**または**UpdateBatch**変更をデータ ソースに送信します。 詳細については、次を参照してください。[更新およびデータの永続化](../../../ado/guide/data/updating-and-persisting-data.md)です。  
  
 これは、コマンド オブジェクトでストアド プロシージャがカーソルの作成が必要ないために、その他の操作を実行するため、更新を実行するストアド プロシージャを使用する方が効率的です。 カーソルの詳細については、次を参照してください。[カーソルとロック](../../../ado/guide/data/understanding-cursors-and-locks.md)です。
