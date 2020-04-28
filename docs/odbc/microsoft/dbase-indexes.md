---
title: dBASE インデックス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9300a38a0e36da771a238f73b77d3dda527334ae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307673"
---
# <a name="dbase-indexes"></a>dBASE インデックス
ODBC dBASE ドライバーが自動的に開き、dBASE IV インデックスファイルが更新されます。 DBASE III. ndx ファイルを dBASE ファイルに関連付けるには、ODBC データソースアドミニストレーターで表示される **[インデックスの選択**] ダイアログボックスを使用する必要があります。  
  
 DBASE インデックスの作成には、次の制限事項が適用されます。  
  
-   すべての列名が有効である必要があります。  
  
-   すべての列は、昇順または降順にする必要があります。  
  
-   1つのテキスト列の長さは100バイト未満である必要があります。  
  
-   複数の列が存在する場合は、すべての列がテキスト列である必要があり、列の合計サイズは100バイト未満である必要があります。  
  
-   メモフィールドにインデックスを設定することはできません。  
  
-   現在のフィールドセットに対してインデックスを指定することはできません (つまり、重複するインデックスは使用できません)。  
  
-   インデックス名は、dBASE インデックスの名前付け規則と一致している必要があります。 dBASE III では、各インデックスが、それぞれ ndx 拡張子を持つ個別のファイルに格納されている必要があります。 DBASE IV では、1つの mdx ファイルに格納されているタグ名としてインデックスが作成されます。 Mdx ファイルには、データベースファイルと同じ基本名が付けられています (たとえば、Emp. mdx は Emp データベースのインデックスファイルです)。  
  
-   dBASE では、一意のインデックスが定義されます。同じキー値を持つセットから1つのレコードのみがインデックスに追加されます。
