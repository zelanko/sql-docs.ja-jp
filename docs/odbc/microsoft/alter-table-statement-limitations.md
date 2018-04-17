---
title: ALTER テーブル ステートメントの制限事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06af545611da90d51ad0fc82136a4cb1ecc3984c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="alter-table-statement-limitations"></a>ALTER テーブル ステートメントの制限事項
ときに、dBASE ファイルまたは Paradox ドライバーが後に使用、インデックスが作成され、新しいレコードを追加、インデックスが削除され、テーブルの内容を削除しない限り、ALTER TABLE ステートメントでテーブルの構造を変更ことはできません。  
  
 Microsoft Excel またはテキストのドライバーは、ALTER TABLE ステートメントはサポートされていません。  
  
> [!NOTE]  
>  Borland データベース エンジンを実装することがなく、Paradox ドライバーを使用する場合、ALTER TABLE ステートメントはサポートされていません。読み取りし、追加のみはステートメントを使用します。
