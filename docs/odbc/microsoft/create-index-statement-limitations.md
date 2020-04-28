---
title: CREATE INDEX ステートメントの制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 053287d5087b377429221c31dd4e6b20f24248e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280883"
---
# <a name="create-index-statement-limitations"></a>CREATE INDEX ステートメントの制限事項
Microsoft Excel またはテキストドライバーでは、CREATE INDEX ステートメントはサポートされていません。  
  
 インデックスは、最大10個の列に定義できます。 CREATE INDEX ステートメントに10個以上の列が含まれている場合、インデックスは認識されず、インデックスが作成されなかったかのように処理されます。  
  
 DBASE ドライバーでは、論理列にインデックスを作成できません。  
  
 DBASE ドライバーを使用すると、SELECT ステートメントの WHERE 句で指定された列 (フィールド) に対して mdx (または ndx) インデックスを作成することによって、大きなファイルの応答時間を向上させることができます。 既存の。 mdx インデックスは、=、>、 \<、>=、=<、および WHERE 句内の演算子と LIKE 述語、および結合述語に対して自動的に適用されます。  
  
 DBASE ドライバーを使用する場合、CREATE UNIQUE INDEX ステートメントによって作成されるインデックスは実際には一意ではなく、インデックス付き列に重複する値を挿入できます。 同じキー値を持つセットから1つのレコードだけをインデックスに追加できます。  
  
 Paradox ドライバーを使用する場合は、テーブル内の列の連続したサブセット (最初の列を含む) に基づいて一意のインデックスを定義する必要があります。 テーブルで一意のインデックスが定義されていない場合、または Borland データベースエンジンを実装せずに Paradox ドライバーを使用する場合は、Paradox ドライバーによってテーブルを更新することはできません。
