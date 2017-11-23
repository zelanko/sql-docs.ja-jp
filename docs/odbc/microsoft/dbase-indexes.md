---
title: "dBASE インデックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8681b981bfeb5f13d6fe10869b1556aecfde9311
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="dbase-indexes"></a>dBASE インデックス
DBASE の ODBC ドライバーは自動的に表示し、dBASE IV のインデックス ファイルを更新します。 使用する必要があります、**インデックスの選択** ダイアログ ボックスを通じて、ODBC データ ソース アドミニストレーターに関連付ける dBASE ファイル dBASE III .ndx ファイルを表示します。  
  
 DBASE インデックスの作成に次の制限事項が適用されます。  
  
-   すべての列名を有効にする必要があります。  
  
-   すべての列は、同じ昇順または降順にする必要があります。  
  
-   任意の 1 つのテキスト列の長さは 100 バイト未満である必要があります。  
  
-   複数の列が存在する場合はテキスト列がありますすべての列と、列のサイズの合計が 100 バイト未満にする必要があります。  
  
-   メモ フィールドのインデックスを付けることはできません。  
  
-   現在のフィールドのセットのインデックスを指定しない必要があります (つまり、重複するインデックスは許可されません)。  
  
-   インデックスの名前は、dBASE インデックスの名前付け規則と一致する必要があります。 dBASE III は .ndx 拡張子を持つ別のファイルに各インデックスにすることが必要です。 DBASE IV、インデックスが 1 つの .mdx ファイルに格納されているタグ名として作成されます。 .Mdx ファイルでは、同じ基本名をデータベース ファイルと (たとえば、Emp.mdx は Emp.dbf データベースのインデックス ファイル)。  
  
-   dBASE は、インデックスに同一のキー値を持つセットから 1 つのレコードを追加する場所として、一意のインデックスを定義します。
