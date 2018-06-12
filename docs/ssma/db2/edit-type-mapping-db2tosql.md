---
title: 型のマッピング (DB2ToSQL) は編集 |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f93c4b7d-74fc-4856-bf42-035289918e83
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bfd91a77ef5abb230277d90cbc068c1794abdb80
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34774528"
---
# <a name="edit-type-mapping-db2tosql"></a>型のマッピング (DB2ToSQL) の編集します。
**型マッピングの編集** ダイアログ ボックスでは、ソースと変換先のデータベース オブジェクト間の種類をマップする方法を指定することができます。  
  
複数の場所でこのダイアログ ボックスを表示できます。  
  
-   ソース データベースまたはデータベース オブジェクトを選択すると、**型マッピング**タブは、メタデータ エクスプ ローラーの右側に表示されます。 をクリックして**追加**を新しい型マッピングを追加する**編集**を既存の型マッピングを変更します。  
  
-   **ツール**メニューの **プロジェクト設定**または**プロジェクト設定の既定の**します。 結果として得られる ダイアログ ボックスで選択**型マッピング**です。 をクリックして**追加**を新しい型マッピングを追加する**編集**を既存の型マッピングを変更します。  
  
テーブルに固有の型マッピングは、データベースをオーバーライドし、プロジェクトの種類のマッピング。 データベース固有のマッピングは、project のマッピングをオーバーライドします。  
  
## <a name="options"></a>および  
**ソースの種類**  
マップするソースのデータ型を選択して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
次のフィールドが表示されます、データ型が可変長の場合は、**ソースの種類**:  
  
**From**  
このマッピングの最小の長さを指定します。 たとえば、 **nchar**データ型を開始位置として、範囲のこのマッピングであることを指定する 10」と入力することができます**nchar(10)** です。  
  
**変換先**  
このマッピングの最大長を指定します。 たとえば、 **nchar**データ型で終わる範囲のこのマッピングであることを指定する 20」と入力することができます**nchar (20) 型**です。  
  
**ターゲットの種類**  
選択、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ソースのデータ型がマップされているデータ型。 SSMA がテーブルまたはストアド プロシージャを作成すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ソースのデータ型は、このデータ型に変更されます。  
  
次のフィールドを下に表示されます、データ型が可変長の場合は、**ターゲット型**:  
  
**Replace with**  
このマッピングのターゲットの長さを指定します。 たとえば、 **nvarchar**データ型に指定したソースのデータ型をマップする必要がありますを指定する 20」と入力することができます**nvarchar (20)** です。  
  
