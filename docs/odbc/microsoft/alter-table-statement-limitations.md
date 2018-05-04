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
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ccff64afd3a4df26b813bb30a84322d50519bd2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="alter-table-statement-limitations"></a>ALTER テーブル ステートメントの制限事項
ときに、dBASE ファイルまたは Paradox ドライバーが後に使用、インデックスが作成され、新しいレコードを追加、インデックスが削除され、テーブルの内容を削除しない限り、ALTER TABLE ステートメントでテーブルの構造を変更ことはできません。  
  
 Microsoft Excel またはテキストのドライバーは、ALTER TABLE ステートメントはサポートされていません。  
  
> [!NOTE]  
>  Borland データベース エンジンを実装することがなく、Paradox ドライバーを使用する場合、ALTER TABLE ステートメントはサポートされていません。読み取りし、追加のみはステートメントを使用します。
