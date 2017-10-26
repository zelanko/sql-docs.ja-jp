---
title: "ALTER テーブル ステートメントの制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6c50ea6550e9dfb255c87886e4e0375240bcd2ae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="alter-table-statement-limitations"></a>ALTER テーブル ステートメントの制限事項
ときに、dBASE ファイルまたは Paradox ドライバーが後に使用、インデックスが作成され、新しいレコードを追加、インデックスが削除され、テーブルの内容を削除しない限り、ALTER TABLE ステートメントでテーブルの構造を変更ことはできません。  
  
 Microsoft Excel またはテキストのドライバーは、ALTER TABLE ステートメントはサポートされていません。  
  
> [!NOTE]  
>  Borland データベース エンジンを実装することがなく、Paradox ドライバーを使用する場合、ALTER TABLE ステートメントはサポートされていません。読み取りし、追加のみはステートメントを使用します。

