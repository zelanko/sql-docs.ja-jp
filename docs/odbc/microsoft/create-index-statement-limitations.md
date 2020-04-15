---
title: インデックス ステートメントの作成の制限 |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280883"
---
# <a name="create-index-statement-limitations"></a>CREATE INDEX ステートメントの制限事項
CREATE INDEX ステートメントは、Excel またはテキスト ドライバーではサポートされていません。  
  
 インデックスは、最大 10 列に定義できます。 CREATE INDEX ステートメントに 10 を超える列が含まれている場合、索引は認識されず、表は索引が作成されなかったかのように扱われます。  
  
 dBASE ドライバーは、論理列のインデックスを作成できません。  
  
 dBASE ドライバーを使用する場合、大きなファイルの応答時間を改善するには、.mdx (または .ndx) インデックスを作成する列 (フィールド) に指定された、SELECT ステートメントの句。 既存の .mdx インデックスは、WHERE 句内の\<=、>、>=、= =< 演算子、および LIKE 述語、および結合述語に自動的に適用されます。  
  
 dBASE ドライバーを使用する場合、CREATE UNIQUE INDEX ステートメントによって作成されたインデックスは、実際には一意ではない、重複する値は、インデックス付きの列に挿入できます。 同じキー値を持つセットから 1 つのレコードのみをインデックスに追加できます。  
  
 Paradox ドライバを使用する場合、テーブル内の列の連続したサブセット (最初の列を含む) に一意のインデックスを定義する必要があります。 テーブルに一意のインデックスが定義されていない場合、またはボーランド データベース エンジンを実装せずに Paradox ドライバーを使用する場合、Paradox ドライバによってテーブルを更新することはできません。
