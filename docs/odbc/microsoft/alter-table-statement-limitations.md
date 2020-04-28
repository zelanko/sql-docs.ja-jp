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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19afa8b07b0051de9ce45ec652ea337c0f689f52
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304701"
---
# <a name="alter-table-statement-limitations"></a>ALTER TABLE ステートメントの制限事項
DBASE または Paradox ドライバーを使用する場合、インデックスが作成され、新しいレコードが追加されると、インデックスが削除され、テーブルの内容が削除されない限り、ALTER TABLE ステートメントでテーブルの構造を変更することはできません。  
  
 Microsoft Excel またはテキストドライバーでは、ALTER TABLE ステートメントはサポートされていません。  
  
> [!NOTE]  
>  Borland データベースエンジンを実装せずに Paradox ドライバーを使用する場合、ALTER TABLE ステートメントはサポートされません。read ステートメントと append ステートメントのみが許可されます。
