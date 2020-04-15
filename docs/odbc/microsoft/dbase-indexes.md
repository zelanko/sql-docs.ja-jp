---
title: dBASE インデックス |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307673"
---
# <a name="dbase-indexes"></a>dBASE インデックス
ODBC dBASE ドライバが自動的に開き、dBASE IV インデックス ファイルが更新されます。 ODBC データ ソース アドミニストレータを使用して表示される **[インデックスの選択**] ダイアログ ボックスを使用して、dBASE III .ndx ファイルを dBASE ファイルに関連付ける必要があります。  
  
 dBASE インデックスの作成には、次の制限が適用されます。  
  
-   すべての列名が有効である必要があります。  
  
-   すべての列は、同じ昇順または降順にする必要があります。  
  
-   1 つのテキスト列の長さは 100 バイト未満でなければなりません。  
  
-   複数の列が存在する場合、すべての列はテキスト列でなければならず、列サイズの合計は 100 バイト未満でなければなりません。  
  
-   メモ型フィールドにはインデックスを付けることができません。  
  
-   現在のフィールドセットに対してインデックスを指定することはできません (つまり、重複するインデックスは許可されません)。  
  
-   インデックス名は dBASE インデックスの命名規則と一致する必要があります。 dBASE III では、各インデックスが個別のファイルに含まれている必要があります。 dBASE IV では、インデックスはタグ名として作成され、単一の .mdx ファイルに格納されます。 .mdx ファイルのベース名はデータベース ファイルと同じです (たとえば、Emp.mdx は Emp.dbf データベースのインデックス ファイルです)。  
  
-   dBASE では、同じキー値を持つセットから 1 つのレコードのみがインデックスに追加される一意のインデックスを定義します。
