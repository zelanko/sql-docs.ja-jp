---
title: ALTER TABLE ステートメントの制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02ce530385cdc911250a81d831dd2fdb81873f76
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63301976"
---
# <a name="alter-table-statement-limitations"></a>ALTER TABLE ステートメントの制限事項
ときに、dBASE ファイルまたは Paradox ドライバーを使って、インデックスが作成され、新しいレコードの追加、インデックスが削除され、テーブルの内容は削除しない限り、ALTER TABLE ステートメントによって、テーブルの構造を変更ことはできません。  
  
 Microsoft Excel またはテキストのドライバーでは、ALTER TABLE ステートメントはサポートされていません。  
  
> [!NOTE]  
>  Borland データベース エンジンを実装することがなく Paradox ドライバーを使用する場合、ALTER TABLE ステートメントはサポートされていません。のみの読み取りし、追加ステートメントを使用できます。
