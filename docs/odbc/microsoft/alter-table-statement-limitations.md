---
title: テーブルステートメントの制限 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19afa8b07b0051de9ce45ec652ea337c0f689f52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304701"
---
# <a name="alter-table-statement-limitations"></a>ALTER TABLE ステートメントの制限事項
dBASE または Paradox ドライバを使用する場合、インデックスが作成され、新しいレコードが追加されると、インデックスが削除されてテーブルの内容が削除されない限り、ALTER TABLE ステートメントでテーブルの構造を変更することはできません。  
  
 EXCEL またはテキスト ドライバーでは、ALTER TABLE ステートメントはサポートされていません。  
  
> [!NOTE]  
>  ボーランド データベース エンジンを実装せずに Paradox ドライバを使用する場合、ALTER TABLE ステートメントはサポートされません。読み取りおよび追加ステートメントのみが許可されます。
