---
title: インデックス ステートメントの制限を作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9501e07fcdb70984153a718eed22be4d5448ec9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-index-statement-limitations"></a>インデックス ステートメントの制限を作成します。
CREATE INDEX ステートメントは、Microsoft Excel またはテキストのドライバーのサポートされていません。  
  
 インデックスは、最大で 10 個の列で定義できます。 CREATE INDEX ステートメントでは、10 個より多くの列が含まれている、インデックスは認識されませんし、テーブルはように扱わインデックスは作成されませんでした。  
  
 DBASE ドライバーは、論理列にインデックスを作成することはできません。  
  
 DBASE ドライバーを使用する場合は、SELECT ステートメントの WHERE 句で指定された列 (フィールド) に .mdx (または .ndx) インデックスを作成して大きなファイル上の応答時間を向上できます。 既存のインデックスを .mdx は =、自動的に適用されます >、 \<、> =、= <、および演算子に、WHERE 句で、LIKE 述語、および結合述語の間です。  
  
 DBASE ドライバーを使用する場合は、CREATE UNIQUE INDEX ステートメントによって作成されたインデックスが実際には一意でないとインデックス付き列に重複する値を挿入できます。 インデックスには、同一のキー値を持つセットから 1 つのレコードを追加できます。  
  
 Paradox ドライバーを使用する場合、連続した最初の列を含め、テーブル内の列のサブセットに一意のインデックスを定義する必要があります。 テーブルまたは Borland データベース エンジンの実装は持たない Paradox ドライバーを使用すると、一意のインデックスが定義されていない場合、Paradox ドライバーによって、テーブルを更新できません。
