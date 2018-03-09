---
title: "レコード セットに関連するエラー情報 |Microsoft ドキュメント"
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
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b1ad53c42fa3da686de10e3254c6fa7e3916d806
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="recordset-related-error-information"></a>レコード セットに関連するエラー情報
バッチ処理中に、**ステータス**のプロパティ、**レコード セット**オブジェクト内の個別のレコードに関する情報を提供する、**レコード セット**です。 バッチ更新が行われる、前に、**ステータス**のプロパティ、 **Recordset**レコードを追加、変更および削除に関する情報が反映されます。 後に**UpdateBatch**が呼び出されて、**ステータス**プロパティは、操作の成否を示します。 レコード間を移動すると、**レコード セット**の値、**ステータス**プロパティの変更は、現在のレコードの状態を説明します。
