---
title: "型のマッピング (AccessToSQL) は編集 |Microsoft ドキュメント"
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
ms.assetid: 7f9d9530-6c04-41d9-bbe7-d91820a30066
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2cfe289d367eee5d33177f8170e4be2919870ada
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="edit-type-mapping-accesstosql"></a>型のマッピング (AccessToSQL) の編集します。
**型マッピングの編集** ダイアログ ボックスでは、ソースと変換先のデータベース オブジェクト間の種類をマップする方法を指定することができます。  
  
複数の場所でこのダイアログ ボックスを表示できます。  
  
-   ソース データベースまたはデータベース オブジェクトを選択すると、**型マッピング**タブは、メタデータ エクスプ ローラーの右側に表示されます。 をクリックして**追加**を新しい型マッピングを追加する**編集**を既存の型マッピングを変更します。  
  
-   **ツール**メニューの **プロジェクト設定**または**プロジェクト設定の既定の**します。 結果として得られる ダイアログ ボックスで選択**型マッピング**です。 をクリックして**追加**を新しい型マッピングを追加する**編集**を既存の型マッピングを変更します。  
  
テーブルに固有の型マッピングは、データベースをオーバーライドし、プロジェクトの種類のマッピング。 データベース固有のマッピングは、project のマッピングをオーバーライドします。  
  
## <a name="options"></a>オプション  
**ソースの種類**  
マップするソースのデータ型を選択して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
次のフィールドが表示されます、データ型が可変長の場合は、**ソースの種類**:  
  
**From**  
このマッピングの最小の長さを指定します。 たとえば、**テキスト**データ型を開始位置として、範囲のこのマッピングであることを指定する 10」と入力することができます**text(10)**です。  
  
**変換先**  
このマッピングの最大長を指定します。 たとえば、**テキスト**データ型で終わる範囲のこのマッピングであることを指定する 20」と入力することができます**text(20)**です。  
  
**ターゲットの種類**  
選択、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ソースのデータ型がマップされているデータ型。 SSMA がテーブルまたはストアド プロシージャを作成すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ソースのデータ型は、このデータ型に変更されます。  
  
次のフィールドを下に表示されます、データ型が可変長の場合は、**ターゲット型**:  
  
**Replace with**  
このマッピングのターゲットの長さを指定します。 たとえば、 **nvarchar**データ型に指定したソースのデータ型をマップする必要がありますを指定する 20」と入力することができます**nvarchar (20)**です。  
  

