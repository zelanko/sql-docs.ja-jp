---
title: "型のマッピング (MySQLToSQL) は編集 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 184f7ab2-725f-491e-a15b-b889f2fb6a68
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ed31beae92c3453917a2fbcfd8ea1643c26a114c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="edit-type-mapping-mysqltosql"></a>型のマッピング (MySQLToSQL) の編集します。
**型マッピングの編集** ダイアログ ボックスでは、ソースと変換先のデータベース オブジェクト間の種類をマップする方法を指定することができます。  
  
複数の場所でこのダイアログ ボックスを表示できます。  
  
-   ソース データベースまたはデータベース オブジェクトを選択すると、**型マッピング**タブは、メタデータ エクスプ ローラーの右側に表示されます。 をクリックして**追加**を新しい型マッピングを追加する**編集**を既存の型マッピングを変更します。  
  
-   **ツール**メニューの **プロジェクト設定**または**プロジェクト設定の既定の**します。 結果として得られる ダイアログ ボックスで選択**型マッピング**です。 をクリックして**追加**を新しい型マッピングを追加する**編集**を既存の型マッピングを変更します。  
  
-   テーブルに固有の型マッピングは、データベースをオーバーライドし、プロジェクトの種類のマッピング。 データベース固有のマッピングは、project のマッピングをオーバーライドします。  
  
## <a name="options"></a>オプション  
  
##### <a name="source-type"></a>ソースの種類  
SQL Server データ型にマップするソースのデータ型を選択します。  
  
次のフィールドが表示されます、データ型が可変長の場合は、 **Sourcetype**:  
  
##### <a name="from"></a>From  
このマッピングの最小の長さを指定します。 たとえば、 **nchar**データ型を開始位置として、範囲のこのマッピングであることを指定する 10」と入力することができます**nchar(10) です。**  
  
##### <a name="to"></a>変換先  
このマッピングの最大長を指定します。 たとえば、 **nchar**データ型で終わる範囲のこのマッピングであることを指定する 20」と入力することができます**nchar (20) 型です。**  
  
##### <a name="target-type"></a>[対象になる種類]  
ソースのデータ型がマップされている SQL Server データ型を選択します。 SSMA は、テーブルを作成するとき、または SQL Server で、ソースのデータ型は、このデータ型に変更されます。  
  
次のフィールドを下に表示されます、データ型が可変長の場合は、**ターゲット型**:  
  
##### <a name="replace-with"></a>[置換後の文字列]  
このマッピングのターゲットの長さを指定します。 たとえば、 **nvarchar**データ型に指定したソースのデータ型をマップする必要がありますを指定する 20」と入力することができます**nvarchar (20)。**  
  

